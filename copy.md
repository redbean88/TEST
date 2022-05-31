Key	Name	Type	Required	Description
organization	기관코드	String	O	
birthDate	생년월일	String	△	[생년월일/주민등록번호], 제한직전 필수 입력하는 기관존재
reqMemberStoreNoList	가맹점번호 목록	Object	O	반복부 키

Key	Name	Type	Required	Description
reqMemberStoreNo	가맹점번호	String	O

Key	Name	Type	Required	Description
reqCount	요청 건수	String	O	
inflowCount	신규등록 건수	String	O	

Key	Name	Type	Required	Description
organization	기관코드	String	O	
reqMemberStoreNoList	가맹점번호 목록	Object	O	반복부 키

Key	Name	Type	Required	Description
reqMemberStoreNo	가맹점번호	String	O	승인내역에서 반환받은 가맹점번호 값을 사용

Key	Name	Type	Required	Description
resMemberStoreNo	가맹점번호	String	O	입력받은 가맹점번호
resMemberStoreName	가맹점명	String	O	
resMemberStoreCorpNo	가맹점 사업자번호	String	O	
resMemberStoreType	가맹점 업종	String	△	
resMemberStoreTelNo	가맹점 전화번호	String	△	
resMemberStoreAddr	가맹점주소	String	△	
resCeoName	대표자	String	△	[대표자명]
resLnkUrl	바로가기	String	△	[홈페이지 주소]
commStartDate	조회시작일자	String	△	[조회기간_시작일자]
commEndDate	조회종료일자	String	△	[조회기간_종료일자]
resResultCode	결과코드	String	O	스크래핑 건별 결과코드 (espider errorCode) : 성공일 경우 0으로
resUserError	UserError	String	O	스크래핑 건별 userError (espider errorCode)
resUserErrorMessage	UserErrorMessage	String	O	스크래핑 건별 userErrorMessage (espider errorCode)
