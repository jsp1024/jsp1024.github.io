---
emoji: 2️⃣
title: 스프링 부트 공부 02
date: '2022-06-14 12:30:00'
author: 박재만
tags: Spring-boot
categories: JAVA
---

## 1. form 태그 사용법

```html
<!--form 태그는 어디로 보낼지의 action과 어떻게 보낼지의 method로 이루어져 있다 -->
<form class="container" action="/articles/create" method="post">
  <div class="mb-3">
    <label class="form-label">제목</label>
    <input type="text" class="form-control" name="title">
  </div>
  <div class="mb-3">
    <label class="form-label">내용</label>
    <textarea class="form-control" rows="3" name="content"></textarea>
  </div>
  <button type="submit" class="btn btn-primary">Submit</button>
</form>
```

## 2. form 데이터 받기
```
@Controller
public class ArticleController {
    @GetMapping("/articles/new")
    public String newArticleForm() {
        return "articles/new";
    }
    @PostMapping("/articles/create")
    public String createArticle() {
        return "";
    }
}
```
폼 데이터를 받기위해 @PostMapping 을 사용하여 url 매핑을 해주었다.

## 3. DTO란?
계층간 데이터(Controller, View 등등)교환을 위한 JAVA 빈즈이다. 
```
private String title;
private String content;

private String title;
    private String content;

    public ArticleForm(String title, String content) {
        this.title = title;
        this.content = content;
    }
```

## 4. toString
* Object 클래스가 가진 메소드
* 객체가 가지고 있는 정보나 값들을 문자열로 만들어 리턴하는 메소드
* Spring boot DTO 클래스에서 사용하는 toString 메소드는 Object 클래스에 있는 
toString() 메소드를 오버라이딩 하여 사용 함(재정의)

폼에 들어있는 정보를 출력하기 위해 println으로 찍어보았다.
```
// view에서 만든 폼 태그의 정보를 PostMapping의 url 주소로 받는다.
    @PostMapping("/articles/create")
    // 그렇게 받아온 데이터는 dto객체에 받아오게 된다.
    public String createArticle(ArticleForm form){
        System.out.println(form.toString());
        return "";
    }
```
이때 form 데이터가 어떤 값인지 정확하게 출력하기 위해서 dto 클래스에 toString()메서드를
추가하여 재정의 해준다.
```
@Override
    public String toString() {
        return "ArticleForm{" +
                "title='" + title + '\'' +
                ", content='" + content + '\'' +
                '}';
    }
```

***
<details>
<summary>출처</summary>
이 글은 유튜버 홍팍(https://www.youtube.com/c/%ED%99%8D%ED%8C%8D)님의
스프링 부트, 입문! 강의를 통해 배운 내용들을 작성하였습니다.

모든 저작권 권한은 홍팍님 에게 있습니다.
</details>
