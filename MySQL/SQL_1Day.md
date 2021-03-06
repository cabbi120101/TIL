## 서버
    - 서버는 우리가 사용하는 컴퓨터를 말한다. 보통 특정 목적을 가지는 컴퓨터를 서버라고 부른다.(예:데이터베이스 서버, 웹서버 등등)

    - 1. 웹서버
        - 웹브라우저와 같은 클라이언트로부터 HTTP 요청을 바고, 웹 페이지를 반환하는 서버.
        - 클라우드 서비스가 많이 활용된다.
        - 클라우드 서비스란 사용자 환경 밖에서 서비스, 컴퓨터 자원을 사용하고 이에 대한 비용을 지불하는 서비스

    - 2. 데이터베이스 서버
        - 데이터베이스 서비스를 다른 컴퓨터나 컴퓨터 프로그램에 제공하는 서비스

## DB GUI Tools


## DBA 
    - DBA(database administrator, DBA)데이터 베이스 관리자, 는 한조직 내에서 데이버베이스를 설치,구성,업그레이드,관리,감시하는 일을 맡은 사람을 가리킨다.

## 개발 및 테스트 지원

## SQL 쿼리 작성법

    - 1. 절차 고민하기
        - 요청사항
            -각각 국가의 연도별 구매자 수를 출력하세요
        - 데이터 탐색
            - 국가 정보, 구매 정보는 어떤 테이블에 존재하는가?
            - 2개 정보가 다른 테이블에 존재한다면 어떻게 결합할 것인가?
            - 칼럼에 중복되는 값이 존재하는가?
        - 쿼리 작성
            - 코객 테이블과 매출 테이블을 결합한다.
            - 국가 칼럼, 연도 칼럼으로 데이터를 그룹핑한다.
            - 구매자 수를 카운트한다.

        - 토입자의 경우 과정을 의식적으로 연습하자

    - 2. 데이터 정합성, 정확성
        - 부분 합과 전체 합 비교하기
        - 분석하기 편한 형태로 데이터 가공하기
        - 리뷰하기


## SQL 문법
    - 되도록 대문자로 입력한다.


    - 1. SELECT
        - SELECT 상품번호
        FROM DB명. PRODUCT;
        - 1. 칼럼 조회
        - 2. 집계 함수
        - 3. *(모든 결과 조회)
        - 4. AS
        - 5. DISTINCT

    - 2. FROM
        - 특정 테이블에 있는 정보를 호출하려면 쿼리에 테이블 명을 지정해 주어야 하는데, 테이블 명은 FROM 절 뒤에 기재해 준다.
        - USE DB 명:
        SELECT 계산식 또는 칼럼 명
        FROM SALES;

    - 3. WHERE
        - SELECT 상품번호
        FROM DB 명.PRODUCT
        WHERE 판매국가 = '미국';
        - 1. BETWEEN
            - 특정 칼럼의 값이 시작점~끝점인 데이터만 출력할 수 있다.
        - 2. 대소 관계 표현
        - 3. IN
        - 4. NOT IN
        - 5. IS NULL
        - 6. LIKE '%TEXT%'
            - %는 문자를 의미, TEXT앞 뒤로 어떤 문자가 와도 상관이 없다란 뜻3
    
    - 4. GROUP BY
        - 칼럼의 값들을 그룹화해 각 값들의 평균 값, 개수등을 구할때 이용하여 계산
        - 제조 국가별, 제조사별 평균 자동차 가격은?
            - SELECT 제조국가,
            제조사명,
            AVG(가격)
            FROM DB명.cars
            GROUP
            BY 제조 국가,
            제조사명;
        - 집계 함수에 CASE WHEN 구문 사용
            - SELECT SUM(CASE WHEN 국가 ='한국' THEN 1 ELSE 0 END) KOREA_CNT
            FORM TABLE;

    - 5. JOIN
        - 1. LEFT JOIN(LEFT OUTER JOIN)
            - 특정 테이블 정보를 기준으로 타 테이블을 결합한다.
            - order(주문 내역)
                - SELECT *
                FROM TABLE_A
                LEFT    JOIN TABLE_B
                ON TABLE_A.Column 1 = TABLE_B.Column 2
                    - 해당 뭐리를 실행하면 TABLE_A의 콜론 1과 TABLE_B의 콜론을 매칭해 동일한 값이 존재하는 TABLE_B의 정보를 출력한다.

        - 2. INNER JOIN
            - 2가지 테이블에 공통으로 존재하는 정보만 출력된다.
        
        - 3. FULL JOIN
            - 매칭되는 레코드를 모두 출력한다.

    - 6. CASE WHEN
        - 조건에 따른 값을 다르게 출력하고 싶은 경우 사용

        - SELECT CASE WHEN 연령 BETWEEN 20 AND 29 THEN '20대'
            WHEN 연령 BETWEEN 40 AND 49 THEN '40대'
            WHEN 연령 BETWEEN 50 AND 59 THEN '50대' END
            FROM DB 명.테이블 명;
                - 위 쿼리를 실행하면 28세는 첫번째 조건을 만족하므로 '20대'라는 값이 출력됨,
                58세는 3번재 조건이므로 '50대'. 위 세가지를 충족 못 시키면 NULL값이 출력됨.
            
    - 7. RANK, DENSE_RANK, ROW_NUMBER
        - 데이터 순위 매기는 함수들
        - ROW_NUMBER()는 동점인 경우도 서로 다른 동수로 계산한다.
        - DENSE_RANK,RANK는 동점인 경우 같은 등수로 계산
            - DENSE_RANK는 동점의 등수 바로 다음 수로 순위를 매긴다.(예; 1등 2등2등 3등)
            - RANK는 동점인 경우의 데이터 세트를 고려해 다음 등수를 매긴다.(예: 1등 2등2등 4등)

    - 8. SUBQUERY
        - IN 연산자 이후 () 내의 쿼리를 쿼리안의 쿼리라는 의미로 subquery라고 한다.
        - IN 뿐만이 아니라 from,join에서도 사용될 수 있다.
            - from에 subquery를 사용하면 서브쿼리의 실행 결과가 하나의 테이블로 사용된다.
            - from,join에 서브쿼리를 사용하는 경우에는 항상 서브쿼리의 마지막에 'A'와 같은 문자열을 입력해 주어야한다.
            - 만약에 A라는 문자열을 입력하면, 해당 테이블은 A라는 명칭으로 쿼리 내부에서 사용된다.



## 3장 

