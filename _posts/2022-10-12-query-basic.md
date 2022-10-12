---
layout: single
title: DB. SQL Query simple
categoires: dev
---

## SELECT

```
//해당 테이블의 해당 컬럼 데이터 불러오기
select 'column_name' from 'table_name';

//해당 테이블의 해당 컬럼에서 해당 조건이 참인 데이터 불러오기
select 'column_name' from 'table_name' where 'column_name=value';

//해당 테이블의 해당 컬럼 해당 조건이 참인 데이터 오름차순 또는 내림차순으로 불러오기
select 'column_name' from 'table_name' where 'column_name=value' order by 'column_name asc or desc';

//해당 테이블의 해당 컬럼 해당 조건이 참인 데이터 오름차순 또는 내림차순으로 개수만큼 불러오기
select 'column_name' from 'table_name' where 'column_name=value' order by 'column_name asc or desc' limit 'number';
```

## INSERT

```
//해당 테이블의 해당 컬럼에 값을 입력하기. 컬럼명과 값의 개수는 같아야한다.
insert into 'table_name' ('column_name1','column_name2','column_name3', ...) values ('value1','value2','value3', ...);

//해당 테이블에 컬럼명 입력 없이 값 입력하기. 테이블의 컬럼의 수와 값의 개수는 같아야한다.
insert into 'table_name' values ('value1','value2','value3', ...);
```

## UPDATE

```
//테이블의 모든 데이터의 컬럼 값을 변경
update 'table_name' set 'column_name=value';

//테이블의 조건에 맞는 데이터의 컬럼 값을 변경
update 'table_name' set 'column_name=value' where 'column_name=value';

//테이블의 조건에 맞는 데이터의 여러 컬럼 값을 변경
update 'table_name' set 'column_name1=value1','column_name2=value2' where 'column_name=value';
```

## DELETE

```
//테이블에 있는 모든 데이터 삭제하기(테이블 삭제랑은 다른 개념)
delete from 'table_name';

//테이블에서 조건에 맞는 데이터만 삭제하기
delete from 'table_name' where 'column_name=value';
```

###### 참고 사이트
[SQL Query문 간단 정리](https://sosobaba.tistory.com/124)