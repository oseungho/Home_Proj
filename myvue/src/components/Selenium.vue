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
                <code style="white-space: pre-wrap;"> 
                    # WebDriver객체 생성
                    driver_path = f'{os.path.join(os.path.dirname(__file__), "chromedriver.exe")}'

                    # 웹드라이버를 위한 Service객체 생성
                    service = Service(executable_path=driver_path)
                    options = webdriver.ChromeOptions()

                    # headless 모드 설정
                    options.add_argument("--headless")  

                    # 사용자 에이전트 설정
                    options.add_argument("user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.0.0 Safari/537.36")  
                    
                    # 자동종료 막기
                    options.add_experimental_option("detach", True)
                    driver = webdriver.Chrome(service=service, options=options)

                    # 브라우저에 페이지 로딩하기
                    driver.get('크롤링을 진행할 URL')
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
    background-color: rgb(220, 216, 211);
    border-radius: 30px;
}
</style>