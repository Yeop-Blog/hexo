---
title: Java에서 사용하는 List에 대해 정리
date: 2017-08-07 01:00:00
tags:
categories: Java
thumbnail: /images/java_thumbnail.jpg
---
출처1 : [http://ledgku.tistory.com/42](http://ledgku.tistory.com/42)<br/>
출처2 : [http://stunstun.tistory.com/193](http://stunstun.tistory.com/193)

보통 많은 데이터를 담거나 보여주거나 할 때 쓰는 것이 List라고 생각한다.<br/>
그런 List의 종류는 아래와 같이 정리해 볼 수 있다.

- Array List(선형 리스트) – 배열을 기반으로 구현한 리스트
- Linked List(연결 리스트) – 메모리 동적 할당을 기반으로 구현한 리스트

위 List들은 Java에서 제공하는 List 인터페이스를 구현한 Collection이다.<br/>

차이점을 말하기전에 앞서 List 인터페이스를 구현하는 ArrayList 또는 LinkedList를 사용하는 이유에 대해서 체크하고 넘어가는 것이 이해하는데 도움이 될 것 같아 출처 부분을 인용하여 작성하고자 한다.

Java에서는 보통 여러 개의 Primitive Type(기본 자료형) 또는 Refrenece Type(인스턴스)을 저장 하기 위해 배열을 사용하곤 한다. 하지만 배열은 초기화 할 때 길이를 초기화 해야 하며, 생성된 배열은 동적으로 변경하기 어렵다는 단점이 있어 데이터 관리 하기에 불편한 점이 있다.

배열과 Vector를 이용한 데이터 관리<br/>

public class ListTest {
	public String[] array = new String[10];
	public Vector<String> vector = new Vector<String>();

	@Test
	public void collectionsTest() {
		System.out.println("Array = " + array.length);
		System.out.println("Vector = " + vector.capacity());
	}
}


이런 부분 때문에 Java 1.0에서는 이러한 문제를 해소 하기 위해 Vector를 주로 사용하고는 했다. 하지만, Vector 역시 초기화 시 10으로 capacity가 정해져, capacity 이상이 되면 2배씩 늘려 나가게 되고 다수의 Thread에 대한 접근에 동기화를 보장하는 등의 성능 이슈 등으로 인해, 1.2이후 Version에서는 호환성을 위해 제공한다고 보면 되며, List 인터페이스를 구현한 List로 대체 되었다.

**ArrayList**<br/>
ArrayList는 내부적으로 자료를 Array(배열) 구조로 가지며, 데이터의 추가/삭제를 위해서는 임시 배열을 생성해 데이터를 복사하는 방법을 사용한다.<br/>
때문에, 대량의 자료를 추가/삭제 하는 경우 성능 저하 현상이 발생할 수 있지만 각 데이터는 Index를 가지고 있기 때문에 한번에 참조가 가능해 데이터 검색에는 유리하다고 볼 수 있다.

**LinkedList**<br/>
LinkedList는 데이터를 저장하는 각 노드가 이전 노드와 다음 노드의 상태만 알고 있다고 보면 된다.<br/>
데이터의 추가/삭제 시에 불필요한 나머지 데이터의 복사가 없으므로 유리하지만, 데이터 검색 시에는 ArrayList와 비교해 불리하다고 볼 수 있다.

즉, 정리하면 다음과 같다.<br/>
ArrayList : Java 1.2에서 추가, 데이터 검색에 유리하며, 추가/삭제는 성능 고려<br/>
LinkedList : Java 1.2에서 추가, 데이터 추가/삭제에 유리하며, 검색은 성능 고려
