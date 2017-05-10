# AngularJS Tutorial

## AngularJS 기본 개념
- [AngularJS 공식 사이트 Conceptual Overview](https://docs.angularjs.org/guide/concepts)

    > Directives : 커스텀 속성과 태그를 사용하는 확장된 HTML.<br>
    > Expressions : 상수 및 변수를 HTML에서 사용 가능

        <p>Hello {{ name }}!</p>        // name이라는 변수를 사용
    
    > Modules : 기능적으로 비슷한 것들끼리 모아 Module을 만든다.<br>
    > Controller : View의 Business Logic을 다루는 데에만 사용<br>
    > Service : 재사용할수 있는 Business Logic<br>

## 개발환경

- [Plunker](https://plnkr.co/)<br>
간단한 프론트엔드 코드를 작성하고 공유할 수 있는 웹 어플리케이션.
    > Plunker의 Editor 메뉴를 이용해, 곧바로 필요한 라이브러리(angularjs, bootstrap 등)응 추가하고 확인할 수 있다.

## 내장 디렉티브
- ng-app : 태그에 해당 디렉티브를 사용하면 해당 태그 내에서는 angular를 사용하겠다고 angular에게 알려줌
- ng-init : javascript 변수나 함수를 초기화 하는데 사용되는 디렉티브

## 표현식
- 중괄호 두개로 변수를 감싸면 변수를 사용할 수 있다.
- 내장 디렉티브와 표현식을 사용한 예시 코드

        <html>
            <head></head>
            <body ng-app ng-init="name='Chris'">
                <h1>Hello {{ name }} !!</h1>
            </body>
        </html>

## 모듈과 컨트롤러
- ng-init은 실제로는 프로토타입을 만들 때 정도에만 사용하고, 실제로는 모듈과 컨트롤러를 사용한다.

> Tip : 모듈과 컨트롤러를 사용할 때에는 클로저를 이용한다. 아래와 같은 형식
 
    (function(){
        // Code Here
    })();

- 모듈 : 큰 개념으로, 이 안에 컨트롤러나 디렉티브 등이 들어있을 수 있다.

        var app = angular.module('todo',[]);
        //  todo라는 이름을 가진 모듈을 생성

- 컨트롤러
    > Tip : Angular에서 컨트롤러의 첫 문자는 대문자로 표시하는 것이 일반적이다.

    1. app.contoller 메서드를 통해 생성
    2. 두 번째 파라미터는 배열
    3. $scope라는 변수는 view단(html)과 컨트롤러를 엮어주는 역할

    >
        // javascript 단
        app.controller('TodoCtrl', ['$scope', function($scope){
            $scope.name = 'Chris'
        }]);
    >
        // html 단
        ...
        <body ng-app="todo" ng-controller="TodoCtrl">
            <h1>Hello {{ name }} !! </h1>
        </body>
        ...

    4. 객체를 선언하는 것도 가능하다.
    >
        // javascript 단
        app.controller('TodoCtrl', ['$scope', function($scope){
            $scope.todo = {
                title: '요가수련',
                completed: false,
                createdAt: Date.now()
            }
        }]);
    >
        //  html 단
        ...
        <body ng-app="todo" ng-controller="TodoCtrl">
            <h1>Todo</h1>

            <h3>{{ todo.title }}</h3>
            <input type="text" ng-model="todo.title">
            <p>{{ todo.completed }}</p>
            <input type="checkbox" ng-model="todo.completed">
            <date>{{ todo.createdAt }}</date>

        </body>
        ...

    > ng-model에 값에 변수를 텍스트 형식으로 넣어두면 텍스트 input의 기본값으로 변수가 들어간다. 그리고 그 변수는 서로 바인딩 되어서 html에서 작동하여 변수가 변경되면 javascript의 변수도 변경됩니다. 이를 양방향 바인딩이라고 합니다.

