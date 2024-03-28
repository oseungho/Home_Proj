<script setup>

</script>

<template>
    <div class="title">
        <h3>Selenium</h3>
        <div style="border: solid 1px gray; border-radius: 15px;">
            <span class="description">
                - 웹 테스트 자동화 도구로 웹드라이버를 통해 브라우저를 제어해서 웹을 테스트하는 용도로 사용하는 라이브러리<br/>
                - BeautifulSoup로 스크래핑이 안되는 동적 페이지나 로그인이 필요한 페이지 등을 스크래핑
            </span>
        </div>
    </div>
    <br/>
    <div class="content">
        <p> 1. 라이브러리 설치 : pip install selenium</p>
        <p> 2. 브라우저 제어 : 
            <pre>
                <code> 
                    pip install selenium
                    pip install selenium
                </code>
            </pre>
        </p>        
    </div>
</template>

<style>
.title{
    text-align: center;
}

.description {
    display: block;
    text-align: left;
    margin: 10px; /* 원하는 여백 추가 */
}

.content{
    padding: 20px;
    border: 1px solid black;
    border-radius: 15px;
}

pre{
    /* width: 50%; */
    background-color: rgb(220, 216, 211);
    border-radius: 30px;
}
</style>