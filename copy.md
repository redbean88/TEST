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
