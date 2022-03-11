# React



#### 1. Element 생성

- Vanila

  ```javascript
  const rootElement = document.getElementById("root");
  const element = document.createElement("h1");
  element.textContent = "Hello, World!";
  rootElement.appendChild(element);
  ```

- React

  ```react
  const rootElement = document.getElementById("root");
  const element = React.createElement("h1", { children: "Hello, World!" });
  ReactDOM.render(element, rootElement);
  ```

  