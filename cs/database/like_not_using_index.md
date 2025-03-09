## LIKE 연산자가 인덱스를 사용하지 않는 이유

> 일반적으로 LIKE 연산자는 특정 패턴을 검색할 때 사용됩니다. 그러나 인덱스를 효율적으로 사용하지 못하는 경우가 많습니다.
>
> 그 이유는 B-Tree 인덱스 구조 및 검색 방식과 LIKE 연산자의 동작 방식이 맞지
> 않기 때문입니다.

<br/>

### LIKE 연산자와 인덱스의 관계

LIKE 연산자가 인덱스를 탈 수 있는 경우와 못 타는 경우를 구분해야 합니다.

1. 인덱스를 타는 경우

```sql
SELECT *
FROM users
WHERE name LIKE 'John%';
```

#### 설명

- B-Tree 인덱스는 왼쪽부터 순차적으로 정렬되어 있기 때문에 'John%'처럼 접두어가 고정된 검색은 효율적으로 인덱스를 탈 수 있습니다.
- name이 B-Tree에 저장되어 있다고 가정하면, "John"을 키로 삼아 빠르게 탐색을 시작할 수 있습니다.

<br/>

2. 인덱스를 못 타는 경우

```sql
SELECT *
FROM users
WHERE name LIKE '%John%';
```

#### 설명

- B-Tree는 왼쪽부터 순차적으로 검색하지만, '%John%'는 문자열 어디에든 "John"이 포함될 수 있으므로 인덱스를 활용할 수 없습니다.
- 결국 모든 데이터를 풀스캔(full scan)하면서 패턴을 검사해야 합니다.
- 즉, LIKE의 앞부분이 가변적이면 인덱스를 사용할 수 없습니다.

<br/>

### 인덱스를 활용하기 위한 방법

1. FULLTEXT 인덱스 활용 (MyISAM, InnoDB 지원)

- MySQL에서는 FULLTEXT 인덱스를 활용하면 부분 문자열 검색('%word%')도 빠르게 수행할 수 있습니다.
- FULLTEXT 인덱스는 자연어 검색을 지원하며, % 없이도 부분 문자열 검색을 빠르게 수행할 수 있습니다.

```sql
ALTER TABLE users ADD FULLTEXT(name);
SELECT * FROM users WHERE MATCH (name) AGAINST('John');
```

<br/>

2. 역순 인덱스 활용

만약 %John과 같은 접미사 기반 검색이 많다면, **역순 인덱스(reverse index)**를 활용할 수도 있습니다.

- name의 역순 문자열을 저장하는 별도의 컬럼(reversed_name)을 만든다.
-  해당 컬럼에 B-Tree 인덱스를 생성한다.
- LIKE '%John'을 실행할 때, 대신 reversed_name LIKE 'nhoJ%' 형태로 변환하여 인덱스를 활용한다.

```sql
ALTER TABLE users ADD COLUMN reversed_name VARCHAR(255);
UPDATE users SET reversed_name = REVERSE(name);
CREATE INDEX idx_reversed_name ON users(reversed_name);
SELECT * FROM users WHERE reversed_name LIKE 'nhoJ%';
```


