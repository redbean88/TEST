Key	Name	Type	Required	Description
connectedId	커넥티드 아이디	String	O	
organization	기관코드	String	O	
birthDate	생년월일	String	△	[생년월일/주민등록번호], 제한직전 필수 입력하는 기관존재(YYYYMMDD)
startDate	시작일자	String	O	yyyyMMdd
endDate	종료일자	String	O	yyyyMMdd
orderBy	일자 정렬 순서	String	O	"0": 최신순, "1": 과거순 (default : "0")
inquiryType	조회구분	String	O	"0": 카드별 조회, "1": 전체조회 (default: "0")
cardNo	카드번호	String	△	카드별 조회시 카드번호 필수 (inquiryType = "0" 인 경우 필수)
KB 카드소지확인 인증이 필요한 경우 필수 : 마스킹 없는 전체 카드번호 입력
cardPassword	카드비밀번호	String	△	KB 카드 소지확인 필요한 경우 : 카드 비밀번호 앞 2자리
cardName	카드명	String	△	(inquiryType == "0")인 경우, 보유카드 조회 결과의 카드명을 사용
duplicateCardIdx	일련번호	String	△	[중복카드 선택 순번]
(inquiryType == "0")인 경우 필수,
"1" 이상: 승인내역 조회 카드목록에서 중복된 카드의 순서
memberStoreInfoType	가맹점정보 포함여부	String	△	"0": 미포함, "1": 가맹점 포함, "2":부가세 포함, "3":전체 (가맹점 +부가세) 포함 (default: "0"
