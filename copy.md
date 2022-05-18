Key	Name	Type	Required	Description
connectedId	커넥티드 아이디	String	O	
organization	기관코드	String	O	
identity	사용자 주민번호/사업자번호	String	△	우리은행의 경우, 비밀번호 오류 3회 이상시 '사업자등록번호' 입력 필요
loginTypeLevel	로그인 권한구분	String	△	"0":이용자, "1":사업장/부서관리자 , "2":총괄관리자 (default: "2")
clientTypeLevel	의뢰인 구분	String	△	[회원구분], "0":신용카드회원, "1":체크카드회원, "2":연구비신용카드회원, "3":프리플러스회원
* 통합 총괄관리자 계정 사용시 필수
startDate	시작일자	String	O	YYYYMMDD
endDate	종료일자	String	O	YYYYMMDD
orderBy	일자정렬순서	String	△	"0": 최신순, "1": 과거순 (default :"0")
inquiryType	조회구분	String	O	"0": 카드별 조회, "1": 전체조회, "2": 부서별 조회
cardNo	카드번호	String	△	(inquiryType = "0" or "3")인 경우 필수
departmentCode	부서코드	String	△	(inquiryType = "2") 인 경우 필수
transeType	거래구분	String	△	[이용지역 거래구분] "0": 전체 조회, "1": 국내/해외 분리 조회 (default: "0")
cardName	카드명	String	△	(inquiryType == "0")인 경우, 보유카드 조회 결과의 카드명을 사용
duplicateCardIdx	일련번호	String	△	[중복카드 선택 순번] (inquiryType == "0")인 경우, "1" 이상: 승인내역 조회 카드목록에서 중복된 카드의 순서
applicationType	신청구분	String	△	"0": 전체 조회, "1": 취소건만 조회 (default: "0")
memberStoreInfoType	가맹점 정보 포함 여부	String	△	"0": 미포함, "1": 가맹점 포함, "2":부가세 포함, "3":전체 (가맹점 +부가세) 포함 (default: "0")
