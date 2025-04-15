### Light Mode (라이트 모드)
+ 기본 밝은 배경 + 어두운 텍스트를 사용하는 사용자 인터페이스(UI)이다.
+ 전통적으로 웹사이트나 앱의 기본 테마이다.

### Dark Mode (다크 모드 / 나이트 모드)
+ 어두운 배경 + 밝은 텍스트를 사용하는 사용자 인터페이스이다.
+ 야간에 눈의 피로를 줄여주고, OLED 화면에서는 배터리 절약 효과도 있다.
+ 최근에는 사용자 편의성 때문에 많은 앱/웹에서 지원하고 있다.

#### index.html
```
<a class="toggle-mode">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 612 612" class="darkmode" id="mode-icon">
        <path fill="var(--ci-primary-color, currentColor)" d="M268.279,496c-67.574,0-130.978-26.191-178.534-73.745S16,311.293,16,243.718A252.252,252.252,0,0,1,154.183,18.676a24.44,24.44,0,0,1,34.46,28.958,220.12,220.12,0,0,0,54.8,220.923A218.746,218.746,0,0,0,399.085,333.2h0a220.2,220.2,0,0,0,65.277-9.846,24.439,24.439,0,0,1,28.959,34.461A252.256,252.256,0,0,1,268.279,496ZM153.31,55.781A219.3,219.3,0,0,0,48,243.718C48,365.181,146.816,464,268.279,464a219.3,219.3,0,0,0,187.938-105.31,252.912,252.912,0,0,1-57.13,6.513h0a250.539,250.539,0,0,1-178.268-74.016,252.147,252.147,0,0,1-67.509-235.4Z" class="ci-primary" style="display: block;" />
    </svg>  
</a>
```
+ svg파일을 다운로드 받아 만든다. 

#### styles.css
```
.toggle-mode {
    max-width: 24px;
    width: 100%;
    height: 24px;
    margin-top: 4px;
}

.darkmode {
    filter: brightness(0) invert(0);
    max-width: 22px;
    width: 100%;
    height: 22px;
    cursor: pointer;
}

.lightmode {
    filter: brightness(0) invert(1);
    max-width: 22px;
    width: 100%;
    height: 22px;
    cursor: pointer;
}
```
+ dark모드이면 filter를 화이트로 변경하기
+ light모드이면 filter를 블랙으로 변경하기

#### main.js
```
// light와 night 모드 설정
const toggleMode = document.querySelector(".toggle-mode");
const darkMode = document.querySelector(".darkmode");

const modeIcon = document.getElementById("mode-icon");


toggleMode.addEventListener("click", ()=> {
    document.body.classList.toggle("night");

    if (darkMode.classList.contains("darkmode")) {
        modeIcon.innerHTML = `<g><g id="Sun"><g>
			<path d="M114.75,286.875H0v38.25h114.75V286.875z M184.614,157.628l-80.937-80.937l-26.985,26.985l80.937,80.937L184.614,157.628
				z M325.125,0h-38.25v114.75h38.25V0z M535.309,103.677l-26.985-26.985l-80.937,80.937l26.985,26.985L535.309,103.677z
				 M497.25,286.875v38.25H612v-38.25H497.25z M306,153c-84.494,0-153,68.506-153,153s68.506,153,153,153s153-68.506,153-153
				S390.494,153,306,153z M306,420.75c-63.38,0-114.75-51.37-114.75-114.75c0-63.38,51.37-114.75,114.75-114.75
				c63.38,0,114.75,51.37,114.75,114.75C420.75,369.38,369.38,420.75,306,420.75z M427.387,454.372l80.937,80.937l26.985-26.985
				l-80.937-80.937L427.387,454.372z M76.691,508.323l26.985,26.985l80.937-80.937l-26.985-26.985L76.691,508.323z M286.875,612
				h38.25V497.25h-38.25V612z"/>
		    </g></g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>
        <g></g>`;

        darkMode.classList.remove("darkmode");   
        darkMode.classList.add("lightmode");


    } else {
        modeIcon.innerHTML = ` <path fill="var(--ci-primary-color, currentColor)" d="M268.279,496c-67.574,0-130.978-26.191-178.534-73.745S16,311.293,16,243.718A252.252,252.252,0,0,1,154.183,18.676a24.44,24.44,0,0,1,34.46,28.958,220.12,220.12,0,0,0,54.8,220.923A218.746,218.746,0,0,0,399.085,333.2h0a220.2,220.2,0,0,0,65.277-9.846,24.439,24.439,0,0,1,28.959,34.461A252.256,252.256,0,0,1,268.279,496ZM153.31,55.781A219.3,219.3,0,0,0,48,243.718C48,365.181,146.816,464,268.279,464a219.3,219.3,0,0,0,187.938-105.31,252.912,252.912,0,0,1-57.13,6.513h0a250.539,250.539,0,0,1-178.268-74.016,252.147,252.147,0,0,1-67.509-235.4Z" class="ci-primary"/>`;

        darkMode.classList.remove("lightmode"); 
        darkMode.classList.add("darkmode");
    }
})
```
+ querySelector 자바스크립트 메소드를 통해서 브라우저에 있는 클래스를 가져온다.
+ toggleMode를 가져와서 클릭하면 classList를 통해서 lightmode 추가하기

