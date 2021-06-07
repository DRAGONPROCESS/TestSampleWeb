<! DOCTYPE html PUBLIC "-// W3C // DTD XHTML 1.0 Strict // EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd" >
<!-url = (0061) https://prosk83.github.io/myweb2/Web_click_Demo_21.03.26.html에서 저장->
< HTML  의 xmlns = " http://www.w3.org/1999/xhtml " XML : LANG = " KO " LANG = " KO " 클래스 = " 번역-LTR " > < 머리 > < 메타  HTTP-당량 = " 내용 -Type " content =" text / html; charset = UTF-8 " >
< title > BrainJar.com : 상품리스트 </ title >

< 링크  HREF = " 파일 : /// C : /common/default.css " 확인해 = " 스타일 " 유형 = " 텍스트 / CSS " >
< 스타일  유형 = " 텍스트 / css " >

/ * 달력 표시 스타일. * /

# calendar {
  border-collapse : 축소;
  국경 간격 :  1 개 픽셀 ;
  여백 :  0 픽셀 ;
  패딩 :  0 픽셀 ;
}

# 달력  tr . header  th {
  배경색 :  # 008080 ;
  색상 :  # ffffff ;
  텍스트 정렬 : 가운데;
}

# 달력  tr . days  th {
  배경색 :  # 80c0c0 ;
  너비 :  2.2 em ;
  텍스트 정렬 : 가운데;
}

# 달력  tr . footer  td {
  테두리 : 없음;
  패딩 :  6 px  0 px  4 px  0 px ;
}

# calendar  td ,  # calendar  th {
  border :  1 px solid # 000000 ;
  색상 :  # 000000 ;
  빈 셀 : 표시;
  패딩 :  2 px  .25 em  2 px  .25 em ;
}

# calendar  td {
  텍스트 정렬 : 오른쪽;
}

# 달력  td . 주말 {
  배경색 :  # e0f0f0 ;
}

# 달력  td . target {
  배경색 :  # ffffe0 ;
  글꼴 두께 : 굵게;
}

# 캘린더  a ,  # 캘린더  a : 방문 {
  색상 :  # 008080 ;
  텍스트 장식 : 없음;
}

# 캘린더  a : hover {
  색상 :  # 0000ff ;
  텍스트 장식 : 없음;
}

# 캘린더  a . 버튼 {
  배경색 :  # 80c0c0 ;
  국경 :  2 픽셀 고체;
  border-color :  # a0e0e0  # 509090  # 509090  # a0e0e0 ;
  색상 :  # 000000 ;
  글꼴 크기 :  80 % ;
  글꼴 두께 : 굵게;
  패딩 :  2 px  .5 em  2 px  .5 em ;
  텍스트 장식 : 없음;
}

# 캘린더  a . 버튼 : 방문 ,  # 캘린더  a . 버튼 : hover {
  색상 :  # 000000 ;
  텍스트 장식 : 없음;
}

</ 스타일 >
< 스크립트  유형 = " text / javascript " > // <! [CDATA [

// ************************************************ *****************************
//이 알림을 제거하지 마십시오.
//
// 저작권 2001 by Mike Hall.
// 사용 약관은 http://www.brainjar.com을 참조하십시오.
// ************************************************ *****************************

// =============================================== ===========================
//이 코드는 달력 표시 및 상호 작용을 처리합니다.
// =============================================== ===========================

// 기본 목표 날짜는 오늘입니다.

var  targetDate  =  new  Date ( ) ;

// 페이지가로드되면 캘린더 표시를 초기화합니다.

창 . onload  =  setCalendar ;

// ------------------------------------------------ ----------------------------
//이 함수는 현재 대상을 반영하도록 달력 표시를 업데이트합니다.
// 데이트.
// ------------------------------------------------ ----------------------------

function  setCalendar ( 이벤트 )  {

  var  el ,  tableEl ,  rowEl ,  cellEl ,  linkEl ;
  var  tmpDate ,  tmpDate2 ;
  var  i ,  j ;

  // 월 이름을 업데이트합니다.

  el  =  문서 . 에서 getElementById ( "calendarHeader" ) . firstChild ;
  el . nodeValue  =  targetDate . getMonthName ( )  +  "\ u00a0"  +  targetDate . getFullYear ( ) ;

  // 매월 1 일부터 시작하여 필요한 경우 뒤로 이동
  // 이전 일요일.

  tmpDate  =  새로운  날짜 ( 날짜 . 구문 분석 ( targetDate ) ) ;
  tmpDate . setDate ( 1 ) ;
  while  ( tmpDate . getDay ( )  ! =  0 )  {
    tmpDate . addDays ( - 1 ) ;
  }

  // 테이블의 각 달력 날짜 셀을 살펴보고 업데이트합니다.

  tableEl  =  문서 . getElementById ( "calendar" ) ;
  for  ( i  =  2 ;  i  <=  7 ;  i ++ )  {
    rowEl  =  tableEl . 행 [ i ] ;

    // 이번 달에 날짜가 없으면 행을 숨 깁니다.

    tmpDate2는  =  새로운  날짜 ( 날짜 . 구문 분석 ( tmpDate ) ) ;
    tmpDate2 . addDays ( 6 ) ;
    if  ( tmpDate . getMonth ( )   ! =  targetDate . getMonth ( )  &&
        tmpDate2 . getMonth ( )  ! =  targetDate . getMonth ( ) )  {
      rowEl . 스타일 . 가시성  =  "숨김" ;
      if  ( document . all )
        for  ( j  =  0 ;  j  <  rowEl . cells . length ;  j ++ )
          rowEl . 세포 [ j ] . 스타일 . borderStyle  =  "없음" ;
    }
    else  {
      rowEl . 스타일 . 가시성  =  "" ;
      if  ( document . all )
        for  ( j  =  0 ;  j  <  rowEl . cells . length ;  j ++ )
          rowEl . 세포 [ j ] . 스타일 . borderStyle  =  "" ;
    }

    // 일주일을 반복합니다.

    for  ( j  =  0 ;  j  <  rowEl . cells . length ;  j ++ )  {
      cellEl  =  rowEl . 세포 [ j ] ;
      linkEl  =  cellEl . firstChild ;

      if  ( tmpDate . getMonth ( )  ==  targetDate . getMonth ( ) )  {
        linkEl . date  =  새  날짜 ( Date . parse ( tmpDate ) ) ;
        s  =  tmpDate . toString ( ) . split ( "" ) ;
        linkEl . 제목  =  s [ 0 ]  +  ""  +  s [ 1 ]  +  ""  +  s [ 2 ]  +  ","  +  s [ s . 길이  -  1 ] ;
        linkEl . firstChild . nodeValue  =  tmpDate . getDate ( ) ;
        linkEl . 스타일 . 가시성  =  "" ;
      }
      그밖에
        linkEl . 스타일 . 가시성  =  "숨김" ;

      // 현재 날짜를 강조 표시합니다.

      if  ( cellEl . oldClass  ==  null )
        cellEl . oldClass  =  cellEl . className ;
      if  ( Date . parse ( tmpDate )  ==  Date . parse ( targetDate ) )
        cellEl . className  =  cellEl . oldClass  +  "대상" ;
      그밖에
        cellEl . className  =  cellEl . oldClass ;

      // 다음 날로 이동합니다.

      tmpDate . addDays ( 1 ) ;
    }
  }
}

// ------------------------------------------------ ----------------------------
// 캘린더 요소에 대한 이벤트 핸들러.
// ------------------------------------------------ ----------------------------

function  addMonths ( 이벤트 ,  n )  {

  // 월을 앞당기 고 디스플레이를 업데이트합니다.

  targetDate . addMonths ( n ) ;
  setCalendar ( 이벤트 ) ;
}

function  addYears ( 이벤트 ,  n )  {

  // 달력 연도를 앞당기 고 디스플레이를 업데이트합니다.

  targetDate . addYears ( n ) ;
  setCalendar ( 이벤트 ) ;
}

function  setTargetDate ( 이벤트 ,  링크 )  {

  // 목표 날짜를 변경하고 달력을 업데이트합니다.

  if  ( 링크 . 날짜  ! =  null )  {
    targetDate  =  새  날짜 ( 날짜 . 구문 분석 ( 링크 . 날짜 ) ) ;
    setCalendar ( 이벤트 ) ;
  }
}

function  displayDate ( 이벤트 )  {

  // 현재 목표 날짜를 형식화 된 문자열로 표시합니다.

  alert ( formatDate ( targetDate ) ) ;
}

function  formatDate ( )  {

  var  mm ,  dd ,  yyyy ;

  // "mm / dd / yyyy"형식으로 목표 날짜를 반환합니다.

  mm  =  문자열 ( targetDate . 속하는 getMonth ( )  +  1 ) ;
  동안  ( mm . 길이  <  2 )
    mm  =  "0"  +  mm ;
  DD  =  문자열 ( targetDate . GETDATE ( ) ) ;
  동안  ( dd . 길이  <  2 )
    dd  =  "0"  +  dd ;
  YYYY  =  문자열 ( targetDate . 하여 getFullYear ( ) ) ;
  동안  ( yyyy . 길이  <  4 )
    yyyy  =  "0"  +  yyyy ;

  return  mm  +  "/"  +  dd  +  "/"  +  yyyy ;
}

// =============================================== ===========================
// Date 객체에 새 속성과 메서드를 추가합니다.
// =============================================== ===========================

// 속성

날짜 . 프로토 타입 . monthNames  =  new  Array ( "January" ,  "February" ,  "March" ,  "April" ,
  "5 월" ,  "6 월" ,  "7 월" ,  "8 월" ,  "9 월" ,  "10 월" ,  "11 월" ,
  "12 월" ) ;
날짜 . 프로토 타입 . savedDate   =  null ;

// 방법

날짜 . 프로토 타입 . getMonthName  =  dateGetMonthName ;
날짜 . 프로토 타입 . getDays       =  dateGetDays ;
날짜 . 프로토 타입 . addDays       =  dateAddDays ;
날짜 . 프로토 타입 . addMonths     =  dateAddMonths ;
날짜 . 프로토 타입 . addYears      =  dateAddYears ;

// ------------------------------------------------ ----------------------------
// getMonthName () : 날짜의 월 이름을 반환합니다.
// ------------------------------------------------ ----------------------------

function  dateGetMonthName ( )  {

   이것을 반환 하십시오 . monthNames [ 이 . getMonth ( ) ] ;
}

// ------------------------------------------------ ----------------------------
// getDays () : 날짜의 월에서 일 수를 반환합니다.
// ------------------------------------------------ ----------------------------

function  dateGetDays ( )  {

  var  tmpDate ,  d ,  m ;

  tmpDate는  =  새로운  날짜 ( 날짜 . 구문 분석 ( 이 ) ) ;
  m  =  tmpDate . getMonth ( ) ;
  d  =  28 ;
  do  {
    d ++ ;
    tmpDate . setDate ( d ) ;
  }  동안  ( tmpDate . 속하는 getMonth ( )  ==  m ) ;

  return  d  -  1 ;
}

// ------------------------------------------------ ----------------------------
// addDays (n) : 날짜에 지정된 일 수를 더합니다.
// ------------------------------------------------ ----------------------------

function  dateAddDays ( n )  {

  // 지정된 일수를 추가합니다.

  이 . setDate ( this . getDate ( )  +  n ) ;

  // 새 날짜를 재설정합니다.

  이 . savedDate  =  이 . getDate ( ) ;
}

// ------------------------------------------------ ----------------------------
// addMonths (n) : 날짜에 지정된 개월 수를 추가하여
// 필요한 경우 해당 월의 날짜입니다.
// ------------------------------------------------ ----------------------------

function  dateAddMonths ( n )  {

  // 아직 설정하지 않은 경우 날짜를 저장합니다.

  if  ( this . savedDate  ==  null )
    이 . savedDate  =  이 . getDate ( ) ;

  // 롤링을 피하기 위해 날짜를 첫 번째로 설정합니다.

  이 . setDate ( 1 ) ;

  // 지정된 개월 수를 추가합니다.

  이 . setMonth ( this . getMonth ( )  +  n ) ;

  // 가능한 경우 저장된 날짜를 복원합니다.

  이 . setDate ( 수학 . 분 ( 이 . savedDate ,  이 . getDays ( ) ) ) ;
}

// ------------------------------------------------ ----------------------------
// addYears (n) : 날짜에 지정된 연도 수를 추가하여
// 윤년의 날짜입니다.
// ------------------------------------------------ ----------------------------

function  dateAddYears ( n )  {

  // 아직 설정하지 않은 경우 날짜를 저장합니다.

  if  ( this . savedDate  ==  null )
    이 . savedDate  =  이 . getDate ( ) ;

  // 롤링을 피하기 위해 날짜를 첫 번째로 설정합니다.

  이 . setDate ( 1 ) ;

  // 지정된 연도를 더합니다.

  이 . 하여 setFullYear ( 이 . 하여 getFullYear ( )  +  N ) ;

  // 가능한 경우 저장된 날짜를 복원합니다.

  이 . setDate ( 수학 . 분 ( 이 . savedDate ,  이 . getDays ( ) ) ) ;
}

//]]> </ 스크립트 >
< 메타  이름 = " 생성기 " 콘텐츠 = " 나모 웹 에디터 v5.0 (평가판) " >
< 링크  유형 = " text / css " rel = " 스타일 시트 " charset = " UTF-8 " href = " ./zzz_files/translateelement.css " > </ head >
< 본체 >

< p  align = " 센터 " > & nbsp; </ p >
< table  id = " calendar " align = " center " >
< tbody > < tr  클래스 = " 헤더 " >
  < th  id = " calendarHeader " colspan = " 7 " > < font  style = " vertical-align : inherit; " > < font  style = " vertical-align : inherit; " > 2021 년 6 월 </ font > </ font > </ 일 >
</ tr >
< tr  class = " 일 " >
  < 제 > < HREF = " https://blog.naver.com/ddangen83/222281050357 " 대상 = " _blank " > < IMG SRC = " ./zzz_files/install_google_white.png " 폭 = " 145 " > </ > </ 일 >  
  < th > < font  style = " vertical-align : inherit; " > < font  style = " vertical-align : inherit; " > 월 </ font > </ font > </ th >
  < th > < font  style = " vertical-align : inherit; " > < font  style = " vertical-align : inherit; " > 화 </ font > </ font > </ th >
  < th > < font  style = " vertical-align : inherit; " > < font  style = " vertical-align : inherit; " > 수요일 </ font > </ font > </ th >
  < th > < font  style = " vertical-align : inherit; " > < font  style = " vertical-align : inherit; " > 목 </ font > </ font > </ th >
  < th > < font  style = " vertical-align : inherit; " > < font  style = " vertical-align : inherit; " > 금 </ font > </ font > </ th >
  < th > < font  style = " vertical-align : inherit; " > < font  style = " vertical-align : inherit; " > 수능 </ font > </ font > </ th >
</ tr >
< tr >
  < TD의  클래스 = " 주말 " > < HREF = " 파일 : /// C : /Users/user/Downloads/sample_html/calendar.html " onclick을 = " setTargetDate (이벤트,이) 반환 거짓; " 스타일 = " 가시성 : 숨김; " > & nbsp; </ a > </ td > 
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 월 Mar 01, 표준시) " style =" visibility : hidden; " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 1 </ font ></ 글꼴 >   </a></td>
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 화 Jun 01, 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 1 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 수요일 Jun 02, 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 2 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 목 Jun 03, 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 삼 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 금 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 4 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = " 주말 " > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " Sat Jun 05, 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 5 </ font > </ font ></ a >   </ td >
</ tr >
< tr >
  < TD의  클래스 = " 주말 " > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " Sun Jun 06, 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 6 </ font > </ font ></ a >   </td>
  < TD의  클래스 = " 타겟 " > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " Mon Jun 07, 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 7 </ font > </ font ></ a >   </td>
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 화 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 8 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 수요일 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 9 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 표준시 6 월 10 일 목요일) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 10 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 표준시 6 월 11 일 금요일) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 11 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = " 주말 " > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " Sat Jun 12, 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 12 </ font > </ font ></ a >   </ td >
</ tr >
< tr >
  < TD의  클래스 = " 주말 " > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " Sun Jun 13, 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 13 </ font > </ font ></ a >   </td>
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 월 표준시) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 14 </ font > </ font > </ a > </ td   >
  < TD의  클래스 = "" > < HREF = " file : ///과 C : /Users/user/Downloads/sample_html/calendar.html " 의 onclick = " setTargetDate (사건이) 복귀는 false " 제목 = " 표준시 6 월 15 일 화요일) " > < font style =" vertical-align : inherit; " > < font style =" vertical-align : inherit; " > 15 </ font > </ font > </ a > </ td   >
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Wed Jun 16, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">16</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="표준시 6 월 17 일 목요일)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">17</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="표준시 6 월 18 일 금요일)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">18</font></font></a></td>
  <td class="weekend"><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Sat Jun 19, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">19</font></font></a></td>
</tr>
<tr>
  <td class="weekend"><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Sun Jun 20, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">20</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Mon Jun 21, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">21</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Tue Jun 22, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">22</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Wed Jun 23, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">23</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="표준시 6 월 24 일 목요일)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">24</font></font></a></td>
  <td class=" target"><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="표준시 6 월 25 일 금요일)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">25</font></font></a></td>
  <td class="weekend"><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Sat Jun 26, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">26</font></font></a></td>
</tr>
<tr>
  <td class="weekend"><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Sun Jun 27, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">27</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Mon Jun 28, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">28</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Tue Jun 29, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">29</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" title="Wed Jun 30, 표준시)"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">30</font></font></a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
  <td class="weekend"><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
</tr>
<tr style="visibility: hidden;">
  <td class="weekend"><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
  <td class=""><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
  <td class="weekend"><a href="file:///C:/Users/user/Downloads/sample_html/calendar.html" onclick="setTargetDate(event, this); return false;" style="visibility: hidden;">&nbsp;</a></td>
</tr>
<tr class="footer">
  <td colspan="2" style="text-align:left;">
    <a class="button" href="file:///C:/Users/user/Downloads/sample_html/calendar.html" title="작년." onclick="addYears(event, -1); return false;"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&lt;&lt; </font></font></a>
    <a class="button" href="file:///C:/Users/user/Downloads/sample_html/calendar.html" title="지난달." onclick="addMonths(event, -1); return false;"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&lt;</font></font></a>
  </td>
  <td colspan="3" style="text-align:center;">
    <a class="button" href="file:///C:/Users/user/Downloads/sample_html/calendar.html" title="강조 표시된 날짜를 사용하십시오." onclick="displayDate(event); return false;"><font style="vertical-align: inherit;"></font></a>
    <font style="vertical-align: inherit;"><a class="button" href="file:///C:/Users/user/Downloads/sample_html/calendar.html" title="Reset calendar to current date." onclick="targetDate = new Date(); setCalendar(event); return false;"><font style="vertical-align: inherit;">재설정 </font></a><a class="button" href="file:///C:/Users/user/Downloads/sample_html/calendar.html" title="Use the highlighted date." onclick="displayDate(event); return false;"><font style="vertical-align: inherit;">선택</font></a></font><a class="button" href="file:///C:/Users/user/Downloads/sample_html/calendar.html" title="달력을 현재 날짜로 재설정합니다." onclick="targetDate = new Date(); setCalendar(event); return false;"><font style="vertical-align: inherit;"></font></a>
  </td>
  <td colspan="2" style="text-align:right;">
    <a class="button" href="file:///C:/Users/user/Downloads/sample_html/calendar.html" title="다음 달." onclick="addMonths(event, 1); return false;"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&gt; </font></font></a>
    <a class="button" href="file:///C:/Users/user/Downloads/sample_html/calendar.html" title="내년." onclick="addYears(event, 1); return false;"><font style="vertical-align: inherit;"><font style="vertical-align: inherit;">&gt;&gt;</font></font></a>
  </td>
</tr>
</tbody></table><div id="goog-gt-tt" class="skiptranslate" dir="ltr"><div style="padding: 8px;"><div><div class="logo"><img src="./zzz_files/translate_24dp.png" width="20" height="20" alt="Google 번역"></div></div></div><div class="top" style="padding: 8px; float: left; width: 100%;"><h1 class="title gray">원본 텍스트</h1></div><div class="middle" style="padding: 8px;"><div class="original-text"></div></div><div class="bottom" style="padding: 8px;"><div class="activity-links"><span class="activity-link">번역 제안하기</span><span class="activity-link"></span></div><div class="started-activity-container"><hr style="color: #CCC; background-color: #CCC; height: 1px; border: none;"><div class="activity-root"></div></div></div><div class="status-message" style="display: none;"></div></div>


<div class="goog-te-spinner-pos"><div class="goog-te-spinner-animation"><svg xmlns="http://www.w3.org/2000/svg" class="goog-te-spinner" width="96px" height="96px" viewBox="0 0 66 66"><circle class="goog-te-spinner-path" fill="none" stroke-width = " 6 " stroke-linecap = " round " cx = " 33 " cy = " 33 " r = " 30 " > </ circle > </ svg > </ div > </ div > </ body > </ html >
