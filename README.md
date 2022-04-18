# 🗳 중고 경매 웹사이트 (3조 팀 프로젝트)
<br>

![메인화면(1)](https://user-images.githubusercontent.com/96467897/162131068-f9d4bff6-01d3-48b4-b8eb-52a75d801c88.png)

## 👨‍👨‍👧 팀원
- 김세린
- 양서영
- 유지연
- 최예진
- 장유진
<br>

## 🗓 프로젝트 기간
- 2022.01.21~2022.02.08 (19일)
<br>

## 📃 프로젝트 개요
- 중고 물품 판매를 경매를 통해 진행할 수 있는 서비스를 제공하는 MVC 패턴 기반 웹 어플리케이션
- 상세 페이지에서 경매 진행 상황 및 남은 시간 실시간 조회 가능
- 낙찰 시, 마이 페이지에서 물품 결제 기능 구현
- 관리자 페이지를 활용한 게시글 블라인드, 회원 경고 가능
<br>

## 🚗 프로젝트 진행방법
- 깃허브를 활용하여 의사소통 진행
  - branch, merge 방법 익숙해지기

- 기능별 역할 분담 
  - 프로젝트 스케치 기능별로 역할을 나누어 진행
  - Frontend, Backend 구분 없이 프로젝트 수행

- 본인이 담당한 부분
  - DB 물품 테이블 inner join을 활용한 메인 페이지의 모든 경매 리스트 조회 기능 구축 (조회 API부터 뷰 렌더링, 페이징)
  - 상세페이지 QnA 게시판 구현에 필요한 DB설정 및 기능 설계
  - 낙찰된 경매 결제 (카카오 API활용)
<br>

## 🛠 기술 스택
- Java
- JavaScript, HTML5, CSS3
- Oracle, SQL
<br>

### 프로젝트 스케치
![프로젝트 스케치](https://user-images.githubusercontent.com/96467897/161971769-ff8e1a46-d8cc-4420-bd76-826f0ab44ddc.PNG)

### ERD
![index MVC](https://user-images.githubusercontent.com/96467897/161972758-a0dfbeaa-ce3b-4321-a358-664dbc10c4de.png)
![Auction MVC](https://user-images.githubusercontent.com/96467897/161972774-88af6fb4-6a96-4b46-a9bb-c5ee9f58b590.png)
## DB
![DB_Diagram](https://user-images.githubusercontent.com/70681797/162094059-342e3f2a-87de-4072-a10b-0bb9245d0a52.png)

|Table|Column|설명|
|---|---|---|
|FTBL_MEMBER|id : 아이디 <br> pwd : 비밀번호  <br> name : 이름 <br> phone : 핸드폰 번호 <br> email : 이메일 주소 <br> type : 회원 유형 구분 <br> warning_cnt : 누적 경고 수 |회원 정보를 저장하는 테이블|
|FTBL_PRODUCT|pd_no : 경매(제품) 번호 <br> id : 등록한 회원 아이디 <br> pd_name : 제품명 <br> hope_price : 경매 희망가 <br> start_price : 경매 시작가 <br> reg_date : 경매 등록일 <br> due_date : 경매 마감일 <br> pd_simple_info : 제품 게시글 제목 <br> pd_info : 제품 소개글 <br> c_no : 카테고리 번호 <br> view_cnt : 누적 조회수 <br> like_cnt : aa <br> sug_cnt : 누적 응찰수 <br> warn_cnt : 게시글 누적 경고수 |경매(제품) 정보를 저장하는 테이블|
|FTBL_PRODUCT_FILE|no : 이미지 고유 번호 <br> pd_no : 해당 이미지의 경매(제품) 번호 <br> file_ori_name : 오리지널 파일 이름 <br> file_save_name : 파일 저장 이름 <br> file_size : 파일 사이즈 |제품 이미지 파일 정보를 저장하는 테이블|
|FTBL_CATEGORY|c_no : 카테고리 번호 <br> category : 카테고리명 |제품 카테고리 분류를 저장하는 테이블|
|FTBL_AUCTION|a_no : 제시가 기록 고유 번호 <br> pd_no : 해당 경매(제품) 번호 <br> id : 제시한 회원 아이디 <br> sug_price : 제시가 <br> sug_date : 제시한 날짜 |경매 응찰 내용을 기록하는 테이블|
|FTBL_HEART|id : 마음 누른 회원 아이디 <br> pd_no : 마음 누른 경매(제품) |마음 누르기(위시리스트)를 기록하는 테이블|
|FTBL_QNA_BOARD|b_no : 질의응답 문의글 고유 번호 <br> id : 질의응답을 작성하는 회원 아이디 <br> pd_no : 질의응답 할 경매(제품) 번호 <br> title : 문의글 제목 <br> content : 문의글 내용 <br> reg_date : 문의글 등록일 <br> group_id : 부모글 <br> depth : 답글 깊이 <br> pos : 답글 순서 |질의응답 문의글 내용을 담는 테이블|
|FTBL_SOLD|s_no : 낙찰 정보 고유 번호 <br> pd_no : 경매(제품) 번호 <br> sug_id : 제시한 회원 아이디 <br> sug_price : 제시가 <br> sug_date : 제시한 날짜 <br> payment : 결제여부 |경매 최종 낙찰 및 결제 유무를 저장하는 테이블|
|FTBL_BLIND|pd_no : 경매(제품) 번호 <br> id : 등록한 회원 아이디 <br> pd_name : 제품명 <br> hope_price : 경매 희망가 <br> start_price : 경매 시작가 <br> reg_date : 경매 등록일 <br> due_date : 경매 마감일 <br> pd_simple_info : 제품 게시글 제목 <br> pd_info : 제품 소개글 <br> c_no : 카테고리 번호 <br> view_cnt : 누적 조회수 <br> like_cnt : aa <br> sug_cnt : 누적 응찰수 <br> warn_cnt : 게시글 누적 경고수 <br> del_date : 블라인드 처리한 날짜 |블라인드 처리한 경매(제품) 정보를 저장하는 테이블|
<br>


## 주요기능

### 경매
- 경매 등록, 수정, 검색
- 경매 참여(제시)
- 마음함(위시리스트) 추가, 제거
- 참여한 경매, 낙찰된 경매 조회
- 낙찰된 경매 결제
- QnA문의글-답글 등록
<br>

### 관리자
- 회원 정보 조회
- 부적절한 경매 블라인드 처리
- 회원(판매자) 경고 처리
<br>


## 메인화면
 
-	디지털기기~기타: 카테고리별 상품 조회
-	Recent : 최근 등록순 상품 조회
-	View: 조회순 상품 조회
-	Heart: 하트순 상품조회
-	신규 경매 : 신규 등록 제품 리스트 탭 활성화
	하트수, 조회수 확인 가능
-	참여한 경매, 경매등록 : 로그인X 시, 로그인 유도 알림창
-	AUCTION NOW : 경매 상품 등록
	로그인 X 시, AUCTION NOW : 로그인/회원가입 유도 알림창
 
-	top suggested: 최근 일주일 내에 제일 많이 제시된 상품 (경매 참여율이 높은 상품들)
-	요즘 뜨는 경매 : 하트순 상품 top 4개
-	오늘의 경매 : 오늘 등록한 상품 top 4개
-	마감임박 경매 : 마감이 빠른 순으로 상품 top 4개  각각의 상품 이름을 누르면 해당 상세 페이지로 이동

# 하단 탭
-	ABOUT US : 사이트 정보
-	CATEGORIES : 카테고리별 경매 리스트 페이지 이동
-	SERVICE : 로그인 시, 마이페이지 이동
-	단, 로그인이 되어있지 않으면 로그인 유도 알림창 

# 검색 기능
-	검색어 입력 시 상품명에 해당 단어가 포함된 경매 목록을 보여줌
-	GET방식을 사용하여 검색 후에도 입력 받은 데이터 유지
 

# 회원가입

-	ajax를 사용하여 키보드 입력을 받을 때 마다 ID 중복 확인
-	모든 칸을 입력 한 후에 ID 사용 가능
	패스워드 일치 시 가입하기 버튼 활성화 
	회원가입 성공 시 로그인 페이지로 이동

#로그인
-	카카오 API 로그인 기능
-	ID 또는 패스워드 오류 시, 로그인 실패 알림창 
-	로그인 성공 시 메인 페이지로 이동


 
# 로그인 후 메인 화면
 
-	현재 로그인 한 사용자의 ID, 로그아웃 버튼, 마이페이지 버튼
-	로그아웃 클릭 시 세션 지워지고, 메인 페이지로 이동
-	마이페이지 클릭 시 현재 사용자의 마이페이지로 이동

# 경매 등록 페이지
 

-	희망가와 시작가는 1000원을 시작으로 500원씩 올라가도록 step 설정
-	마감일 등록 시, 최소 날짜는 현재날짜 +1
	최대 날짜는 현재 날짜 + 20일로 설정
-	카테고리 선택가능 
-	jpg, png 이미지 파일 업로드 가능
-	경매 물품 등록 완료 시, 경매 상세페이지로 이동

# 경매 상세페이지
 
-	경매마감일 실시간으로 출력
-	제품 정보, 시작가, 희망가 출력
-	QnA 토글 클릭 시, QnA 목록 출력 
-	수정하기 : 입력 폼 수정 가능
-	RELATED PRODUCTS : 동일한 판매자의 다른 상품들을 보여줌

# 경매 참여
 
-	제시가 키보드로 입력 가능
	+,- 버튼 누를 시 1000원씩 증감 가능
-	경매 진행 현황에서 현재 제시가 TOP3 내역 및 회원 아이디 확인 가능
-	ADD TO HEART 
	♡를 누르면 ♥로 변경 후 하단의 ♥ + 1
	(마이페이지의 내 마음함에서 확인가능)
-	CANCEL TO HEART
	♥에서 ♡로 변경되며 하단의 ♥ - 1 
	단, 내 게시글에는 하트 누르기 불가능)

#마이페이지
 
-	사용자의 정보, 등록한 경매, 마음함으로 이동

# 내 정보
 
-	사용자의 ID, 이름, 전화번호, 이메일, 경고 수 확인 가능
-	내 정보 수정 버튼 클릭 시 내 정보 수정 페이지로 이동
-	내 계정 삭제 버튼 클릭 시 내 계정 삭제 페이지로 이동

#내가 등록한 경매
 
-	로그인한 사용자가 등록한 경매 목록을 보여줌
-	상품명 클릭 시 해당 경매의 상세페이지로 이동
-	수정하기 버튼 클릭 시 해당 경매의 수정하기 페이지로 이동

#내 마음함
 
-	사용자가 마음함에 추가한 경매 목록을 보여줌
-	상품명 클릭 시 해당 경매의 상세페이지로 이동
-	페이징 기능

# 참여한/낙찰된 경매
 
-	현재 사용자가 참여한 경매 목록을 보여줌
-	상품명 클릭 시 해당 경매의 상세페이지로 이동
 
-	현재 사용자가 참여했던 경매 중 낙찰된 경매 목록을 보여줌
-	결제하기 버튼 클릭 시 나오는 QR코드를 휴대폰으로 스캔하거나, 카카오 계정 정보를 입력할 경우 카카오페이 결제 화면으로 이동

# 결제 기능
 
-	KAKAO PAY API 기능
-	낙찰된 해당 경매의 정보를 받아와 카카오 머니(테스트용 가상 계좌)로 결제

 
-	결제가 완료되면 웹에서 결제완료 페이지 출력
-	메인으로 가기 버튼 클릭 시 메인으로 이동

# 관리자 기능

-	관리자 계정으로 로그인 시 회원관리, 경매관리 버튼 보여줌
-	회원관리 버튼 클릭 시 전체 회원 조회 페이지로 이동
-	경매관리 버튼 클릭 시 블라인드 게시물 목록 페이지로 이동
-	경매 상세보기, 경매 검색 가능
-	경매 등록 불가

# 전체 회원 조회

-	전체 회원에 대한 ID, 이름, 전화번호, 이메일, 경고 수 확인 가능


 

#블라인드 기능
 
-	경매 상세페이지에서 블라인드 처리하기 버튼 클릭 시 알림창이 뜸
-	확인 클릭 시 해당 게시물은 블라인드 게시판으로 이동하고, 경매중인 목록에서 볼 수 없음

 
-	블라인드 처리 된 게시물에 대한 번호, 회원ID, 제품명, 분류, 희망가, 시작가, 등록일, 마감일, 삭제일(블라인드 처리된 날짜) 확인 가능
-	경매가 블라인드 처리될 시 해당 경매의 판매자는 경고 1회
	경고 5회 누적 시 로그인 불가

# QnA 게시판
 
-	QnA 토글 클릭 시 해당 경매의 게시판 목록을 보여줌
-	문의글 작성 클릭 시  QnA 문의글 등록 폼으로 이동
-	게시판 목록에서 제목 클릭 시 글 상세 내용으로 이동
	해당 경매의 판매자만 답글 작성 가능
-	게시글에 대한 답글 등록 시, 해당 게시글 바로 아래에 [Re] 답글이 추가됨

 
-	작성자 : 현재 로그인한 사용자ID
-	문의등록 클릭 시 문의글이 등록되며 QnA목록으로 이동
-	전체삭제 클릭 시 입력한 내용 리셋 됨
-	취소 클릭 시 상세페이지로 이동

 
-	문의글 상세 내용 확인 가능
-	답글 클릭 시 답글 등록 폼 생성
-	목록 클릭 시 해당 경매의 QnA 목록으로 이동

-	해당 경매의 판매자만 답글 등록 가능
-	답글 등록 클릭 시 등록되며 QnA 목록으로 이동
-	취소 클릭 시 해당 경매의 QnA 목록으로 이동



## 💊 보완할 점
- 관리자 페이지 기능 다양화
  - 직접 회원 신고 기능 추가 : 현재 게시물을 통해 1회 경고 가능, 다양한 방법으로 관리 기능 활성화 필요
- 낙찰 시, 낙찰자에게 알람 기능 추가
- 판매 후처리 관련
  - 직거래 vs 택배 : 경매 낙찰 이후 물품 거래 방법 모호
  - 직거래로 하는 경우, 채팅 기능을 추가하여 직거래 위치 조정
  - 택배로 하는 경우, 결제 시 배송지 입력
- QnA 게시판 ajax를 통한 비 동기식 동작 구현 시도 (현재, JSP 동기식 구현) 
