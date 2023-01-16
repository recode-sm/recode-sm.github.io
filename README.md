# 설비 보전 경험 지식 공유 플랫폼 API
&nbsp; &nbsp; 
&nbsp; &nbsp; 
&nbsp; &nbsp; 

## 1. 경험지식 요청 리스트 전체 조회

### Request

`GET https://{domain}/project9/getDataQnaListAll`

&nbsp; &nbsp;
### Parameters

| 이름 | 데이터명 | 유형 | 필수여부 |
|------|---|---|:---:|
| user_token | String | 외부 사용자 인증키 | O |
| keyword | String | 검색어 | |
| industry_gubun | String | 산업군 | |
| process_gubun | String| 상세 공정 | |
| broken_sh | String | 고장 상황 | |
| broken_hs | String | 고장 현상 | |

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|qna_list|요청글 목록| |
|qna_idx|요청글 순번|int|
|usernm|작성자|String|
|industry_gubun_name|산업군|String|
|process_gubun_name|상세공정|String|
|broken_sh_name|고장상황|String|
|broken_hs_name|고장현상|String|
|title|제목|String|
|content|내용|String|
|job_dt|작성일시|String|
|finish_yn|채택여부|int|
|reply_count|답변수|int|


&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function getDataQnaListAll(){
    var search ={
        user_token:" eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        keyword: '',
        industry_gubun: '',
        process_gubun: '',
        broken_sh: '',
        broken_hs: ''
    }
    $.ajax({
        url: "https://{domain}/project9/getDataQnaListAll",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: search,
        success:function(response){
            console.log(response)
        }
    });
}
```


&nbsp; &nbsp; 
&nbsp; &nbsp;       
## 2. 경험지식 요청 글 상세 조회

### Request

`GET https://{domain}/project9/getDataQnaReply`

&nbsp; &nbsp;
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|qna_idx|String|요청 글 번호|O|

&nbsp; &nbsp; 
### Response

|이름|데이터명|유형|
|------|---|---|
|industry_gubun_name|산업군|String|
|process_gubun_name|상세공정|String|
|model|모델명|String|
|model_com|모델제조사|String|
|model_create_dt|제조일자|String|
|model_install_dt|설치일자|String|
|broken_sh_name|고장상황|String|
|broken_hs_name|고장현상|String|
|title|제목|String|
|content|내용|String|
|job_dt|작성일시|String|
|finish_yn|채택여부|int|
|reply_count|답변수|int|
|**fileList**|**첨부 파일 목록**| |
|ata_org_name|파일 이름|String|
|ata_size|파일 크기|int|
|ata_path|다운로드 주소|String|
|**replyList**|**답변 순번 목록**| |
|reply_idx|답변 순번|int|
|content_reply|답변 내용|String|
|job_dt|답변 작성 일시|String|
|selected|채택 유무|String|
|usernm|답변 장성자|String|
|user_gubun_name|답변자 구분|String|
|**replyFileList**|**답변 첨부 파일 목록**| |
|rata_org_name|파일 이름|String|
|rata_size|파일 크기|int|
|rata_path|다운로드 주소|String|
|message|결과 안내문|String|
|result|결과 코드|int |

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function getDataQnaReply(){
    var search ={
        user_token:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        qna_idx: 34
    }
    $.ajax({
        url: "https://{domain}/project9/getDataQnaReply",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: search,
        success:function(response){
            console.log(response)            
        }
    });
}
```

&nbsp; &nbsp; 
&nbsp; &nbsp; 
## 3. 경험지식 – 요청 등록

### Request

`POST https://{domain}/project9/insertDataQna_attach`

&nbsp; &nbsp;
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|industry_gubun|String|산업군| |
|process_gubun|String|상세 공정|O|
|broken_sh|String|고장 상황|O|
|broken_hs|String|고장 현상| |
|model|String|모델명| |
|model_com|String|모델제조사| |
|model_create_dt|String|제조일자| |
|model_install_dt|String|설치일자| |
|mold_break_yn|String|금형파손여부| |
|title|String|제목|O|
|content|String|내용|O|
|qna_attach|File|첨부파일| |

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function insertDataQna_attach(){
    var f = new FormData($('#form1')[0]);
    $.ajax({
        url: "https://{domain}/project9/insertDataQna_attach",
        type: "post",
        enctype: 'multipart/form-data',
        async: false,
        crossDomain: true,
        daraType: "json",
        processData: false,
        contentType: false,
        data: f,
        success:function(response){
            console.log(response)           
        }
    });
}

<form id="form1" name="form1" method="post" enctype="multipart/form-data">   
    <label>사용자 토큰</label>   
    <input type="text" name="user_token" value="eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
       eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
       iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8">"><br>
    <label>산업군</label>
    <input type="text" name="industry_gubun"><br>
    <label>상세 공정</label>
    <input type="text" name="process_gubun"><br>
    <label>고장 상황</label>
    <input type="text" name="broken_sh"><br>
    <label>고장 현상</label>
    <input type="text" name="broken_hs"><br>
    <label>모델명</label>
    <input type="text" name="model"><br>
    <label>모델 제조사</label>
    <input type="text" name="model_com"><br>
    <label>제조 일자</label>
    <input type="date" name="model_create_dt"><br>
    <label>설치 일자</label>
    <input type="date" name="model_install_dt"><br>
    <label>금형파손여부</label>
    <input type="text" name="mold_break_yn"><br>
    <label>제목</label>
    <input type="text" name="title"><br>
    <label>내용</label>
    <textarea name="content"></textarea><br>
    <label>첨부파일</label>
    <input type="file" name="qna_attach" multiple>
</form>
```

&nbsp; &nbsp; 
&nbsp; &nbsp;
## 4. 경험지식 – 경험 지식 수정

### Request

`GET https://{domain}/project9/updateMyQna`

&nbsp; &nbsp;
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|qna_idx|int|요청 글 번호|O|
|industry_gubun|int|산업군| |
|process_gubun|int|상세 공정|O|
|model|String|모델명| |
|model_com|String|모델제조사| |
|model_create_dt|String|제조일자| |
|model_install_dt|String|설치일자| |
|mold_break_yn|String|금형파손여부| |
|broken_sh|int|고장 상황|O|
|broken_hs|int|고장 현상| |
|title|String|제목|O|
|content|String|내용|O|

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function updateMyQna(){
    var search ={
        user_token:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        qna_idx: '61',
        industry_gubun: '1',
        process_gubun: '2',
        broken_sh: '3',
        broken_hs: '1',
        model: 'ABC',
        model_com: 'ABC',
        model_create_dt: '2012-11-11',
        model_install_dt: '2012-11-11',
        out_temp: '20',
        out_hmdt: '30',
        mold_break_yn: '1',
        title: '오일받이 누수',
        content: ' 바닥이 지저분해요'
    }
    $.ajax({
        url: "https://{domain}/project9/updateMyQna",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: search,
        success:function(response){
            console.log(response)           
        }
    });
}
```

&nbsp; &nbsp; 
&nbsp; &nbsp; 
## 5. 경험지식 – 답변 등록

### Request

`POST https://{domain}/project9/insertDataReply_attach`

&nbsp; &nbsp;
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|qna_idx|String|요청글 번호|O|
|content_reply|String|답변 내용|O|
|reply_attach|File|첨부파일| |

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function insertDataReply_attach(){
    var f = new FormData($('#form2')[0]);
    $.ajax({
        url: "https://{domain}/project9/insertDataReply_attach",
        type: "POST",
        enctype: 'multipart/form-data',
        async: false,
        crossDomain: true,
        daraType: "json",
        processData: false,
        contentType: false,
        data: f,
        success:function(response){
            console.log(response)
        }
    });
}

<form id="form2" name="form2" method="post" enctype="multipart/form-data">
<label>사용자 토큰</label>   
    <input type="text" name="user_token" value="eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
    eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
    iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8"><br>
    <label>요청글 순번</label>
    <input type="text" name="qna_idx" value="73"><br>
    <label>내용</label>
    <textarea name="content_reply"></textarea><br>
    <label>첨부파일</label>
    <input type="file" name="reply_attach" multiple>
</form>
```

&nbsp; &nbsp; 
&nbsp; &nbsp; 
## 6. 경험지식 – 답변 수정

### Request

`GET https://{domain}/project9/updateDataReply`

&nbsp; &nbsp; 
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|reply_idx|String|답변 번호|O|
|content_reply|String|답변 내용|O|

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function updateDataReply(){
    var search ={
        user_token:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        reply_idx: 59,
        content_reply: '수정 내용'
    }
    $.ajax({
        url: "https://{domain}/project9/updateDataReply",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: search,
        success:function(response){
            console.log(response)
        }
    });
}
```

&nbsp; &nbsp; 
&nbsp; &nbsp; 
## 7. 경험지식 – 답변 삭제

### Request

`GET https://{domain}/project9/deleteDataReply`

&nbsp; &nbsp;
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|reply_idx|String|답변 번호|O|

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function deleteDataReply(){
    var search ={
        user_token:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        reply_idx: 60
    }
    $.ajax({
        url: "https://{domain}/project9/deleteDataReply",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: search,
        success:function(response){
            console.log(response)
        }
    });
}
```

&nbsp; &nbsp; 
&nbsp; &nbsp;
## 8. 경험지식 – 나의 경험 지식 리스트 조회

### Request

`GET https://{domain}/project9/getMyDataQnaList`

&nbsp; &nbsp; 
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|page|int|페이지 번호| |

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|totalPage|총 페이지 수|int|
|nowPage|현재 페이지 번호|int|
|my_qna_list|나의 요청글 목록| |
|qna_idx|요청글 순번|int|
|usernm|작성자|String|
|industry_gubun_name|산업군|String|
|process_gubun_name|상세공정|String|
|broken_sh_name|고장상황|String|
|broken_hs_name|고장현상|String|
|title|제목|String|
|content|내용|String|
|job_dt|작성일시|String|
|finish_yn|채택여부|int|
|reply_count|답변수|int|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function getMyDataQnaList(){
    var search ={
        user_token:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        page: ''
    }
    $.ajax({
        url: "https://{domain}/project9/getMyDataQnaList",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: search,
        success:function(response){
            console.log(response)
            
        }
    });
}
```

&nbsp; &nbsp; 
&nbsp; &nbsp; 
## 9. 경험지식 – 고객센터 글 등록

### Request

`GET https://{domain}/project9/insertDataHelp`

&nbsp; &nbsp;
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|brdtitle|String|글 제목|O|
|brdmemo|String|글 내용|O|

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function insertDataHelp(){
    var f ={
        user_token:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        brdtitle: '외부 문의 등록',
        brdmemo: '문의 내용'        
    }
    $.ajax({
        url: "https://{domain}/project9/insertDataHelp",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: f,
        success:function(response){
            console.log(response)           
        }
    });
}
```

&nbsp; &nbsp; 
&nbsp; &nbsp;
## 10. 경험지식 – 고객센터 리스트 조회

### Request

`GET https://{domain}/project9/getDataHelpList`

&nbsp; &nbsp;
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|page|int|페이지 번호| |
|keyword|String|검색어| |

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|totalPage|총 페이지 수|int|
|nowPage|현재 페이지 번호|int|
|help_list|고객센터 글 목록| |
|brdno|글 순번|String|
|brdtitle|글 제목|String|
|usernm|작성자|String|
|brdhit|조회수|String|
|replycnt|답변수|String|
|brddate|작성일|String|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function getDataHelpList(){
    var search ={
        user_token:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ.
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        page: '',
        keyword:''
    }
    $.ajax({
        url: "https://{domain}/project9/getDataHelpList",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: search,
        success:function(response){
            console.log(response)
        }
    });
}
```

&nbsp; &nbsp; 
&nbsp; &nbsp;
## 11. 경험지식 – 고객센터 글 상세 조회

### Request

`GET https://{domain}/project9/getDataHelpOne`

&nbsp; &nbsp;
### Parameters

|이름|데이터명|유형|필수여부|
|------|---|---|:---:|
|user_token|String|외부 사용자 인증키|O|
|brdno|String|글 번호|O|

&nbsp; &nbsp;
### Response

|이름|데이터명|유형|
|------|---|---|
|totalPage|총 페이지 수|int|
|nowPage|현재 페이지 번호|int|
|help_list|고객센터 글 목록| |
|brdno|글 순번|String|
|brdtitle|글 제목|String|
|usernm|작성자|String|
|brdhit|조회수|String|
|replycnt|답변수|String|
|brddate|작성일|String|
|message|결과 안내문|String|
|result|결과 코드|int|

&nbsp; &nbsp;
### Jquery 코드 샘플

```javascript 
function getDataHelpOne(){
    var search ={
        user_token:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
        eyJ1c2Vybm8iOjg1LCJ1c2VyaWQiOiJkbXRlazEwNiIsImlhdCI6MTY3MDk4MjY0MSwiZXhwIjoxNjc4NzU4NjQxfQ. 
        iWSLtvLgUFAw8ODaDDURcILvOqJEYnx5kjOd6AZhTg8",
        brdno: '47'
    }
    $.ajax({
        url: "https://{domain}/project9/getDataHelpOne",
        type: "GET",
        async: false,
        crossDomain: true,
        daraType: "json",
        contentType: "text/plain",
        mimeType: "text/plain",
        data: search,
        success:function(response){
            console.log(response)            
        }
    });
}
```
