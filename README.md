# 아라의 심플 계산기

아라의 심플 계산기는 **JavaScript, HTML, CSS**만을 사용하여 구현된 기본 계산기입니다. 이 프로젝트는 초보자를 위한 간단한 계산기 로직 이해와 DOM 조작 학습을 목표로 제작되었습니다.

## 🌟 주요 기능

1. **사칙연산**:
   - 덧셈, 뺄셈, 곱셈, 나눗셈을 지원합니다.
2. **실시간 디스플레이 업데이트**:
   - 버튼 클릭 시 입력 값과 결과를 화면에 즉시 반영합니다.
3. **초기화 기능**:
   - `C` 버튼을 눌러 계산 상태를 초기화할 수 있습니다.
4. **에러 처리**:
   - `0`으로 나누는 경우 "Error" 메시지를 출력합니다.
5. **깔끔하고 직관적인 UI**:
   - 노란색과 연보라색을 테마로 한 아름다운 인터페이스.

---

## 📋 코드 개요

### HTML
- **구조**:
  - 계산기의 디스플레이와 숫자, 연산자, 초기화 버튼을 배치.
  - 각 버튼은 클릭 이벤트를 통해 기능을 수행합니다.

```html
<div id="calculator">
  <div id="display">0</div>
  <button>1</button>
  <button>2</button>
  <button>3</button>
  <button>+</button>
  <button>4</button>
  <button>5</button>
  <button>6</button>
  <button>-</button>
  <button>7</button>
  <button>8</button>
  <button>9</button>
  <button>x</button>
  <button>0</button>
  <button>c</button>
  <button>=</button>
  <button>/</button>
</div>
```

<hr>

### CSS
+ 디자인 테마:
노란색과 연보라색 계열의 밝고 화사한 색상 조합.
+ 버튼에 호버 및 클릭 효과 추가.
+ 디스플레이 영역을 강조하여 가독성 향상.

<hr>

### JavaScript
+ 핵심 로직:
입력된 숫자와 연산자를 기반으로 계산 결과를 도출.
사용자 인터랙션에 따라 실시간으로 상태 업데이트.

```javascript
const display = document.querySelector("#display");
let currentInput = "";
let previousInput = "";
let operator = null;

function handleNumber(num) {
  currentInput += num;
  updateDisplay(currentInput);
}

function handleOperator(op) {
  if (currentInput === "" && operator) return;
  if (currentInput === "") return;
  if (previousInput && currentInput && operator) calculate();
  previousInput = currentInput;
  currentInput = "";
  operator = op;
}

function calculate() {
  if (!previousInput || !currentInput || !operator) return;

  const prev = parseFloat(previousInput);
  const current = parseFloat(currentInput);

  const operations = {
    "+": (a, b) => a + b,
    "-": (a, b) => a - b,
    x: (a, b) => a * b,
    "/": (a, b) => (b === 0 ? "Error" : a / b),
  };

  currentInput = operations[operator]?.(prev, current) ?? "Error";
  operator = null;
  previousInput = "";
  updateDisplay(currentInput);
}

function clearCalculator() {
  currentInput = "";
  previousInput = "";
  operator = null;
  updateDisplay("0");
}

function updateDisplay(value) {
  display.textContent = value;
}
```
<hr>

### 🛠️ 기술 스택
HTML5: 구조 설계
CSS3: 사용자 인터페이스 스타일링
JavaScript (Vanilla JS): 계산기 로직 구현

<hr>

### 🚀 프로젝트 목표
DOM 조작 학습:
JavaScript를 활용해 버튼 클릭 이벤트와 화면 업데이트를 구현.
조건문과 함수 활용:
숫자 입력, 연산자 처리, 계산 수행 등 각 기능을 독립적으로 구현.
UI/UX 개선:
CSS를 통해 사용자 친화적인 인터페이스 설계.

<hr>

### 🖼️ 실행 결과

![image](https://github.com/user-attachments/assets/94f4c110-f6a0-492d-a056-5ace52c6c1f1)

<hr>

### ✨ 배운 점
JavaScript의 조건문과 함수 활용법.
HTML과 CSS를 사용한 인터페이스 설계.
DOM 이벤트 처리와 상태 관리의 중요성.

<hr>

### 🔮 개선 아이디어
1. 키보드 입력 지원:
사용자가 키보드로 계산기를 조작할 수 있도록 이벤트 추가.
2. 반응형 디자인:
다양한 화면 크기에서도 최적의 사용 경험 제공.
3. 고급 연산 추가:
제곱근, 퍼센트 계산,연산자의 우선순위 별 계산 등 고급 기능 추가.


