## SQL - JOIN

### 1. INNER JOIN

- 동일한 값이 있는 행만 반환한다.

    ![image](https://user-images.githubusercontent.com/61968474/130625394-8769f4d8-c5be-4ab3-9425-c9601c98b96f.png)

    ```sql
    SELECT 컬럼명 [, 컬럼명]
    FROM 테이블A  
    [INNER] JOIN 테이블B ON 테이블A.조인키컬럼 = 테이블B.조인키컬럼;
    ```

### 2. LEFT OUTER JOIN

- 기준 테이블의 값 + 기준 테이블과 중복된 값
- 왼쪽 테이블을 기준으로 OUTER JOIN 하는 것
- LEFT JOIN = LEFT OUTER JOIN

    ![image](https://user-images.githubusercontent.com/61968474/130626138-14e4b9a7-88d4-4911-9b0d-334f48640ebd.png)

    ```SQL
    SELECT 컬럼명 [, 컬럼명]
    FROM 테이블A  
    LEFT OUTER JOIN 테이블B ON 테이블A.조인키컬럼 = 테이블B.조인키컬럼;
    ```


### 3. RIGHT OUTER JOIN

- 오른쪽 테이블을 기준으로 OUTER JOIN 하는 것

    ![image](https://user-images.githubusercontent.com/61968474/130626448-b549bb3b-6822-4451-a95a-c01d94549f4f.png)


    ```SQL
    SELECT 컬럼명 [, 컬럼명]
    FROM 테이블A  
    RIGHT OUTER JOIN 테이블B ON 테이블A.조인키컬럼 = 테이블B.조인키컬럼;
    ```

### 4. FULL OUTER JOIN

- 두 테이블의 합집합

    ![image](https://user-images.githubusercontent.com/61968474/130626698-7d9531b2-dbe2-4f5b-ba6f-5f5fc0df6a1b.png)

    ```SQL
    SELECT 컬럼명 [, 컬럼명]
    FROM 테이블A  
    FULL OUTER JOIN 테이블B ON 테이블A.조인키컬럼 = 테이블B.조인키컬럼;
    ```

### 5. CROSS JOIN

- 모든 경우의 수 조합
- 결과는 (A테이블 행의 갯수 * B테이블 행의 갯수)

    ![image](https://user-images.githubusercontent.com/61968474/130626871-819a07d0-4816-480a-8e33-a54c0f7826d9.png)

    ```SQL
    SELECT 컬럼명 [, 컬럼명]
    FROM 테이블A
    CROSS JOIN 테이블B
    ```

### 6. SELF JOIN
- 자기 자신과 조인하는 것

    ![image](https://user-images.githubusercontent.com/61968474/130627281-96182ac6-6fe4-4c47-a115-ce6c44939913.png)

    ```SQL
    SELECT A.NAME, B.AGE
    FROM TABLE_A A, TABLE_A B;
    ```

### 7. NATURAL JOIN
- 두 테이블 간의 동일한 이름을 갖는 모든 컬럼들에 대해 조인한다.
- USING, ON, WHERE 절 사용 X
- SQL Server는 지원 X

    ```SQL
    SELECT 컬럼명
    FROM 테이블A
    NATURAL JOIN 테이블B
    ``