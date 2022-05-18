Key	Name	Type	Required	Description
resUsedDate	사용일자	String	O	 
resUsedTime	사용일시	String	△	 
resCardNo	카드번호	String	△	 
resCardNo1	카드번호1	String	△	주1) 가맹점정보 포함하여 조회할 경우 매출전표에 있는 카드번호
resCardName	카드명	String	△	 
resMemberStoreName	가맹점명	String	△	 
resUsedAmount	이용금액	String	O	[승인금액]
resPaymentType	결제방법	String	O	"1":일시불, "2":할부, "3":그외
resInstallmentMonth	할부개월	String	△	할부건인 경우 필수
resAccountCurrency	통화코드	String	O	KRW: 한국원화, JPY: 일본 엔, USD: 미국 달러, EUR: 유로... ( ISO 4217 코드)
resApprovalNo	승인번호	String	△	 
resPaymentDueDate	결제예정일	String	△	 
resHomeForeignType	국내/외 구분	String	O	"1":국내, "2":해외
resMemberStoreCorpNo	가맹점 사업자번호	String	△	<memberStoreInfoType = "1" or "3" 인경우>
resMemberStoreType	가맹점 업종	String	△	<memberStoreInfoType = "1" or "3" 인경우>
resMemberStoreTelNo	가맹점 전화번호	String	△	<memberStoreInfoType = "1" or "3" 인경우>
resMemberStoreAddr	가맹점 주소	String	△	<memberStoreInfoType = "1" or "3" 인경우>
resMemberStoreNo	가맹점 번호	String	△	가맹점번호 또는 가맹점 정보조회시 필요 데이터. 해외건 또는 미승인내역의 경우 미제공
resCancelYN	취소여부	String	O	"0": 정상, "1": 취소, "2": 부분취소, "3": 거절
resCancelAmount	취소금액	String	△	취소건인 경우만 제공
resVAT	부가세	String	△	<memberStoreInfoType = "2" or "3" 인경우>
resCashBack	봉사료	String	△	<memberStoreInfoType = "2" or "3" 인경우>
resKRWAmt	원화금액	String	△	 
commStartDate	시작일자	String	O	(요청일 기준 최대 조회 가능시작일, YYYYMMDD)
commEndDate	종료일자	String	O	(YYYYMMDD)

Key	Name	Type	Required	Description
connectedId	커넥티드 아이디	String	O	
organization	기관코드	String	O	
cardNo	카드번호	String	△	KB 카드소지확인 인증이 필요한 경우 필수 : 마스킹 없는 전체 카드번호 입력
cardPassword	카드비밀번호	String	△	KB 카드 소지확인 필요한 경우 : 카드 비밀번호 앞 2자리
birthDate	생년월일	String	△	[생년월일/주민등록번호], 제한직전 필수 입력하는 기관존재(YYYYMMDD)
startDate	시작일자	String	△	청구년월 (YYYYMM), 미입력시 최근 명세서 조회
memberStoreInfoYN	가맹점정보 포함여부	String	△	"0": 미포함, "1": 가맹점 포함 (default: "0")

Key	Name	Type	Required	Description
resPaymentDueDate	결제예정일	String	O	YYYYMMDD
resWithdrawalDueDate	출금예정일	String	△	YYYYMMDD
resTotalAmount	합계금액	String	O	총결제금액
resBillType	명세서구분	String	△	명세서구분 또는 발급사등 구분
resPaymentAccount	결제계좌	String	O	은행명 계좌번호
resAmountOutstanding	미결제금액	String	△	[전월 미결제금액]
resLateFee	연체료	String	△	[전월 연체료]
resFullAmt	일시불(금액)	String	△	
resInstallmentAmt	할부(금액)	String	△	
resCashService	현금서비스(금액)	String	△	[단기카드대출(현금서비스)]
resCardLoan	카드론	String	△	[장기카드대출(카드론)]
resRevolving	리볼빙	String	△	[일부결제금액이월약정(리볼빙)]
resAnnualFee	연회비	String	△	
resPreWithdrawal	기출금액	String	△	
resOverseasUse	해외이용	String	△	[해외이용금액]
resMinDepositAmt	최소 입금금액	String	△	
resChargeHistoryList	청구내역 반복부 키	Object	O	

Key	Name	Type	Required	Description
resUsedDate	사용일자	String	△	
resUsedCard	이용카드	String	△	
resPaymentType	결제방법	String	O	"1":일시불, "2":할부, "3":그외, "4":단기카드대출, "5":장기카드대출
resMemberStoreName	가맹점명	String	O	
resUsedAmount	이용금액	String	△	
resInstallmentMonth	할부개월	String	△	할부건인 경우 필수
resRoundNo	회차	String	△	할부건인 경우 필수
resPaymentPrincipal	결제금액_원금	String	△	
resFee	수수료	String	△	수수료/ 선입금/ 할인, 면제등
resPaymentAmt	결제금액	String	△	
resAfterPaymentBalance	결제후잔액	String	△	
resEarnPoint	적립포인트	String	△	
resMemberStoreCorpNo	가맹점 사업자번호	String	△	memberStoreInfoYN = 1인 경우
resMemberStoreType	가맹점 업종	String	△	memberStoreInfoYN = 1인 경우
resMemberStoreTelNo	가맹점 전화번호	String	△	memberStoreInfoYN = 1인 경우
resMemberStoreAddr	가맹점 주소	String	△	memberStoreInfoYN = 1인 경우
resMemberStoreNo	가맹점 번호	String	△	memberStoreInfoYN = 1인 경우
resApprovalNo	승인번호	String	△	memberStoreInfoYN = 1인 경우
