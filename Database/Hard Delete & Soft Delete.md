# Hard Delete & Soft Delete

*Assembled by GimuneLee (2020-01-13)*

<br/>

## Hard Delete

- **일반적인 삭제**
- Soft Delete의 반대 개념이라는 의미로 'Hard'를 붙인 것
- SQL DELETE 문 사용

<br/>

## Soft Delete

- 일반적인 삭제 대신 `removed` 컬럼을 갱신(SQL UPDATE 문 사용)하는 방식입니다.

- 컬럼명은 보통 `removed` , `deleted_at` , `is_deleted` 를 사용합니다.

- 컬럼의 자료형은 `boolean` 또는 `datetime` 사용합니다.

  ex) 삭제되지 않은 데이터는 `removed` 컬럼값이 **NULL** , 삭제된 데이터는 `removed` 값이 **삭제된 일시**

- 복구하거나 예전 기록을 확인하고자 할 때 간편합니다.

- 다른 테이블과 JOIN 시에 항상 `removed` 를 점검해야 하므로 불편하며 속도도 느립니다.

<br/>

## SQL 문 비교

### Hard Delete (일반적인 삭제)

```sql
DELETE FROM customer WHERE id=112;
```

### Soft Delete

```sql
UPDATE customer SET deleted=NOW() WHERE id=112;
```

Soft Delete에서 삭제를 구분하는 컬럼의 타입은 `boolean` 보다는 `datetime` (삭제된 시간)을 많이 사용한다고 합니다.

<br/>

## Reference & Additional Resources

- [https://zetawiki.com/wiki/%EC%86%8C%ED%94%84%ED%8A%B8_%EC%82%AD%EC%A0%9C,_%ED%95%98%EB%93%9C_%EC%82%AD%EC%A0%9C](https://zetawiki.com/wiki/소프트_삭제,_하드_삭제)