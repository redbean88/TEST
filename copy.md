Key	Name	Type	Required	Description
connectedId	커넥티드 아이디	String	O	
organization	기관코드	String	O	
identity	사용자 주민번호/사업자번호	String	△	우리은행의 경우, 비밀번호 오류 3회 이상시 '사업자등록번호' 입력 필요
loginTypeLevel	로그인 권한구분	String	△	"0":이용자, "1":사업장/부서관리자 , "2":총괄관리자 (default: "2")
clientTypeLevel	의뢰인 구분	String	△	[회원구분], "0":신용카드회원, "1":체크카드회원, "2":연구비신용카드회원, "3":프리플러스회원
* 통합 총괄관리자 계정 사용시 필수
orderBy	일자 정렬 순서	String	O	
"0": 최신순, "1": 과거순 (default :"0")
inquiryType	조회구분	String	O	
"0": 카드별 조회, "2": 부서별조회
cardNo	카드번호	String	△	
(inquiryType = "0")인 경우 필수
departmentCode	부서코드	String	△	
(inquiryType = "2")인 경우 필수

Key	Name	Type	Required	Description
resUsedDate	사용일자	String	O	 
resUsedTime	사용일시	String	O	 
resCardNo	카드번호	String	O	 
resMemberStoreName	가맹점명	String	O	 
resUsedAmount	이용금액	String	O	 
resPaymentType	결제방법	String	O	"1":일시불, "2":할부, "3":그외
resInstallmentMonth	할부개월	String	△	결제방법이 할부일 경우 필수
resAccountCurrency	통화코드	String	O	
KRW: 한국원화, JPY: 일본 엔, USD: 미국 달러, EUR: 유로... ( ISO 4217 코드)
resApprovalNo	승인번호	String	O	 
resHomeForeignType	국내/외 구분	String	O	"1":국내, "2":해외
resCancelYN	취소여부	String	O	
"0": 정상, "1": 취소, "2": 부분취소, "3": 거절
resCancelAmount	취소금액	String	△	 
