---
title: Union으로 테이블(Table) 결합하여 조회하기
thumbnail: /images/tip_thumbnail.jpg
date: 2017-10-01 16:46:00
categories:
- Tip's
tags:
---
- 출처 : http://lab.cliel.com/284

Union은 두개 이상의 Table을 결합하여 마치 하나의 Table처럼 조회할 수 있도록 합니다. Table을 결합한다는 의미에서는 Join과 비슷하지만 Join과는 전혀 다른 개념이 적용되므로 주의하시기 바랍니다.

### Union
먼저 다음 두개의 Table을 살펴보겠습니다.
~~~sql
Select * From Person.BusinessEntityAddress
Select * From Person.BusinessEntityContact
~~~
{% img 1.jpg /images/post_images/old-blog-post45-1.jpg 첫번째 이미지 %}

위의 두 Table에서 BusinessEntityID열만을 조회하여 보도록 하겠습니다. 이때 Union문을 통해 두 Table을 결합합니다.
~~~sql
Select BusinessEntityID
From Person.BusinessEntityAddress
Union
Select BusinessEntityID
From Person.BusinessEntityContact
~~~
{% img 2.jpg /images/post_images/old-blog-post45-2.jpg 두번째 이미지 %}

위에서 처럼 Union을 통해 각각의 Table을 결합하여 조회하려면 조회하고자 하는 Table의 열 형식이 같아야 합니다.(열의 이름은 상관없습니다.) 단, 형식이 같아야 한다는 조건은 조회하고자 하는 열에만 해당합니다. 조회대상이 아닌 열은 포함되지 않아도 됩니다.
~~~sql
Select MakeFlag
From Production.Product
Union
Select FolderFlag
From Production.Document
~~~
{% img 3.jpg /images/post_images/old-blog-post45-3.jpg 세번째 이미지 %}

이때 조회될때 표시되는 열 이름은 첫번째 Table의 열이름으로 정해지게 됩니다.

또한 Union사용시 Data정렬순서를 지정하고자 한다면 Union대상의 Table마다 일일이 Order By를 지정해 줄 필요없이 마지막 Table에만 Order By를 지정해 주시면 됩니다.

위 예제에서 Person.BusinessEntityAddress Table의 행은 19614행이고 Person.BusinessEntityContact Table은 909행이었으나 Union된 결과는 19579행입니다. 결과가 이렇게 되는 이유는 Union을 통해 Table이 결합되면 열값이 같은 경우(조회 대상이 열에 한하여) 중복해서 표시하지 않기 때문입니다.

### Union All
Union을 통해 Table결합하여 조회하는 경우 중복값은 생략하고 결과를 표시하였습니다. 반면 Union All은 모든 테이블의 데이터를 생략없이 전부 조회하게 됩니다.
~~~sql
Select BusinessEntityID
From Person.BusinessEntityAddress
Union All
Select BusinessEntityID
From Person.BusinessEntityContact
Order By BusinessEntityID
~~~
{% img 4.jpg /images/post_images/old-blog-post45-4.jpg 네번째 이미지 %}
