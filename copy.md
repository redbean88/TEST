Key	Name	Type	Required	Description
resUsedDate	사용일자	String	O	
resUsedTime	사용일시	String	△	
resCardNo	카드번호	String	O	
resMemberStoreAddr	가맹점 주소	String	△	<memberStoreInfoType = "1" or "3" 인경우>
resMemberStoreName	가맹점명	String	△	
resUsedAmount	이용금액	String	O	[승인금액]
resPaymentType	결제방법	String	O	1:일시불, "2":할부, "3":그외
resInstallmentMonth	할부개월	String	△	결제방법이 할부건인 경우 필수
resAccountCurrency	통화코드	String	O	
resApprovalNo	승인번호	String	△	
resPaymentDueDate	결제예정일	String	△	
resMemberStoreNo	가맹점 번호	String	△	
resMemberStoreCorpNo	가맹점 사업자번호	String	△	<memberStoreInfoType = "1" or "3" 인경우>
resMemberStoreType	가맹점 업종	String	△	<memberStoreInfoType = "1" or "3" 인경우>
resHomeForeignType	국내/외 구분	String	O	"1":국내, "2":해외
resMemberStoreTelNo	가맹점 전화번호	String	△	<memberStoreInfoType = "1" or "3" 인경우>
resCancelYN	취소여부	String	O	"0": 정상, "1": 취소, "2": 부분취소, "3": 거절
* 부분취소 : 부분취소에 대한 명확한 구분이 가능할 경우 (사이트 부분취소 정보제공 시)혹은,
승인/취소건이 한건으로 제공되는 기관의 경우는 승인 값보다 취소값이 적은경우 해당 값으로 제공
resCancelAmount	취소금액	String	△	
resVAT	부가세	String	△	<memberStoreInfoType = “2" or "3" 인경우>
resCashBack	봉사료	String	△	<memberStoreInfoType = “2" or "3" 인경우>
resKRWAmt	원화금액	String	△	해외 승인일 경우만 제공
resFee	수수료	String	△	
commStartDate	시작일자	String	O	요청일 기준 최대 조회 가능시작일, YYYYMMDD
commEndDate	종료일자	String	O	YYYYMMDD

Key	Name	Type	Required	Description
connectedId	커넥티드 아이디	String	O	
organization	기관코드	String	O	
identity	사용자 주민번호/사업자번호	String	△	우리은행의 경우, 비밀번호 오류 3회 이상시 '사업자등록번호' 입력 필요
loginTypeLevel	로그인 권한구분	String	△	"0":이용자, "1":사업장/부서관리자 , "2":총괄관리자 (default: "2")
clientTypeLevel	의뢰인 구분	String	△	[회원구분], "0":신용카드회원, "1":체크카드회원, "2":연구비신용카드회원, "3":프리플러스회원
* 통합 총괄관리자 계정 사용시 필수
startDate	시작일자	String	△	청구년월 (YYYYMM), 미입력시 최근 명세서 조회
inquiryType	조회구분	String	△	0: 카드별 조회, "1": 전체조회 (default:0)
cardNo	카드번호	String	△	카드별 조회시 필수
memberStoreInfoType	가맹점정보 포함여부	String	△	"0": 미포함, "1": 가맹점 포함 (default: "0"

Key	Name	Type	Required	Description
resPaymentDueDate	결제예정일	String	O	YYYYMMDD
resWithdrawalDueDate	출금예정일	String	△	YYYYMMDD
resTotalAmount	합계금액	String	O	총결제금액
resBillType	명세서구분	String	△	현대카드 [청구구분]
resPaymentAccount	결제계좌	String	△	은행명 계좌번호
resDepartmentCode	부서코드	String	△	
resDepartmentName	부서명	String	△	
resCardNo	카드번호	String	△	
resDomesticUse	국내이용	String	△	
resOverseasUse	해외이용	String	△	[해외이용금액]
resAnnualFee	연회비	String	△	
resAmountOutstanding	미결제금액	String	△	[전월 미결제금액]
resLateFee	연체료	String	△	[전월 연체료]
resPreWithdrawal	기출금액	String	△	
resFullAmt	일시불(금액)	String	△	
resInstallmentAmt	할부(금액)	String	△	
resCashService	현금서비스(금액)	String	△	[단기카드대출(현금서비스)]
resChargeHistoryList	청구내역 반복부 키	Object	O

Key	Name	Type	Required	Description
resUsedDate	사용일자	String	△	
resUsedCard	이용카드	String	△	
resMemberStoreName	가맹점명	String	O	
resMemberStoreCorpNo	가맹점 사업자번호	String	△	
resMemberStoreAddr	가맹점 주소	String	△	
resUsedAmount	이용금액	String	△	
resInstallmentMonth	할부개월	String	△	할부건인 경우 필수
resRoundNo	회차	String	△	할부건인 경우 필수
resPaymentPrincipal	결제금액_원금	String	△	
resFee	수수료	String	△	
resPaymentAmt	결제금액	String	△	
resLocalAmt	현지금액	String	△	해외 결제건인 경우만 제공
resAccountCurrency	통화코드	String	△	현지금액 통화코드
resAfterPaymentBalance	결제후잔액	String	△	
resEarnPoint	적립포인트	String	△	
resMemberStoreType	가맹점 업종	String	△	memberStoreInfoType = "1"인 경우
resMemberStoreTelNo	가맹점 전화번호	String	△	memberStoreInfoType = "1"인 경우
resMemberStoreNo	가맹점 번호	String	△	memberStoreInfoType = "1"인 경우
resApprovalNo	승인번호	String	△	memberStoreInfoType = "1"인 경우
resCancelAmount	취소금액	String	△	[매출취소

Key	Name	Type	Required	Description
connectedId	커넥티드 아이디	String	O	
organization	기관코드	String	O	
identity	사용자 주민번호/사업자번호	String	△	우리카드의 경우, 비밀번호 오류 3회 이상시 '사업자등록번호' 입력 필요
loginTypeLevel	로그인 권한구분	String	△	"0":이용자, "1":사업장/부서관리자 , "2":총괄관리자 (default: "2")
clientTypeLevel	의뢰인 구분	String	△	[회원구분], "0":신용카드회원, "1":체크카드회원, "2":연구비신용카드회원, "3":프리플러스회원
* 통합 총괄관리자 계정 사용시 필수
startDate	시작일자	String	O	(YYYYMMDD), 롯데카드의 경우 결제년월(YYYYMM)
endDate	종료일자	String	△	YYYYMMDD
orderBy	일자 정렬 순서	String	O	
"0": 최신순, "1": 과거순 (default :"0")
inquiryType	조회구분	String	O	
"0": 카드별 조회, "1": 전체조회 (default: "0")
cardNo	카드번호	String	△	
(inquiryType = "0")인 경우 필수
memberStoreInfoType	가맹점정보 포함여부	String	△	
"0": 미포함, "1": 가맹점 포함 (default: "0"

Key	Name	Type	Required	Description
resUsedDate	사용일자	String	O	 
resUsedTime	사용일시	String	△	 
resCardNo	카드번호	String	O	 
resMemberStoreName	가맹점명	String	O	 
resUsedAmount	이용금액	String	O	 
resPaymentType	결제방법	String	O	
1:일시불, "2":할부, "3":그외
resInstallmentMonth	할부개월	String	△	
결제방법이 할부일 경우 필수
resAccountCurrency	통화코드	String	O	 
resApprovalNo	승인번호	String	△	 
resPaymentDueDate	결제예정일	String	△	[결제일]
resHomeForeignType	국내/외 구분	String	O	"1":국내, "2":해외
resCancelYN	취소여부	String	O	"0": 정상, "1": 취소, "2": 부분취소, "3": 거절
* 부분취소 : 부분취소에 대한 명확한 구분이 가능할 경우 (사이트 부분취소 정보제공 있을 시)
resCancelDate	취소일자	String	△	 
resCancelAmount	취소금액	String	△	 
resKRWAmt	원화금액	String	△	<해외건>
resFee	수수료	String	△	 
resPurchaseDate	매입일자	String	△	 
resUseNation	이용국가	String	△	<해외건>
resMemberStoreType	가맹점업종	String	△	
<memberStoreInfoType = "1"인 경우>
resMemberStoreNo	가맹점번호	String	△	
<memberStoreInfoType = "1"인 경우>
resMemberStoreCorpNo	가맹점사업자번호	String	△	
<memberStoreInfoType = "1"인 경우>
resMemberStoreTelNo	가맹점전화번호	String	△	
<memberStoreInfoType = "1"인 경우>
resMemberStoreAddr	가맹점주소	String	△	
<memberStoreInfoType = "1"인 경우>
resForeignReceiptAmt	해외접수금액	String	△	<해외건>
resAccountCurrency1	통화코드1	String	△	
<해외건>, [해외접수금액 통화코드]
resExchangeRate	환율	String	△	<해외건>
commStartDate	시작일자	String	O	
(요청일 기준 최대 조회 가능시작일, YYYYMMDD)
commEndDate	종료일자	String	O	(YYYYMMDD
