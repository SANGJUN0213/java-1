# java-1
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>JavaScript & DOM Examples</title>
</head>
<body>
 
  <h2>1. DOM 조작</h2>
  <div id="myDiv">Original Content</div>
  <button onclick="changeContent()">Change Content</button>
  
  <h2>2. DOM 선택자 문제</h2>
  <div id="exampleId">This is ID</div>
  <div class="exampleClass">Class 1</div>
  <div class="exampleClass">Class 2</div>

  <h2>3. DOM 이벤트 문제</h2>
  <button id="myButton">Click Me</button>
  
  <h2>4. BOM 문제</h2>
  <button onclick="redirectPage()">Go to Google</button>

  <h2>5. BOM History 문제</h2>
  <button onclick="goBack()">Go Back</button>
  <button onclick="goForward()">Go Forward</button>
  
  <h2>6. CSSOM 문제</h2>
  <div id="styledDiv">This is a div</div>
  <button onclick="changeStyle()">Change Style</button>

  <h2>7. Reflow와 Repaint 문제</h2>
  <ul id="itemList"></ul>

  <h2>8. JavaScript 실행 맥락 문제</h2>
  <pre>실행 맥락: 전역과 함수의 차이</pre>

  <h2>9. 콜 스택 문제</h2>
  <pre>함수 호출 순서: first -> second -> third</pre>

  <h2>10. 이벤트 루프 문제</h2>
  <pre>Start -> End -> Timeout finished</pre>

  <script>
    function changeContent() {
      document.getElementById("myDiv").innerHTML = "New Content!";
    }

    const elementById = document.getElementById("exampleId");
    console.log(elementById.textContent);

    const elementBySelector = document.querySelector(".exampleClass");
    console.log(elementBySelector.textContent);

    const elementsByClass = document.getElementsByClassName("exampleClass");
    console.log(elementsByClass[0].textContent);
    console.log(elementsByClass[1].textContent);

    const button = document.getElementById("myButton");
    button.addEventListener("click", function() {
      console.log("Button clicked!");
    });

    function redirectPage() {
      window.location.href = "https://www.google.com";
    }

    function goBack() {
      history.back();
    }

    function goForward() {
      history.forward();
    }

    function changeStyle() {
      const div = document.getElementById("styledDiv");
      div.style.color = "red";
      div.style.fontSize = "20px";
    }

    function addItems() {
      const fragment = document.createDocumentFragment();
      for (let i = 0; i < 10   ; i++) {
        const li = document.createElement('li');
        li.textContent = `Item ${i}`;
        fragment.appendChild(li);
      }
      document.getElementById("itemList").appendChild(fragment);
    }
    addItems();

    function first() {
      console.log("First function");
      second();
    }

    function second() {
      console.log("Second function");
      third();
    }

    function third() {
      console.log("Third function");
    }
    first();  

    console.log("Start");
    setTimeout(function() {
      console.log("Timeout finished"); 
    }, 2000);
    console.log("End");

  </script>
</body>
</html>
