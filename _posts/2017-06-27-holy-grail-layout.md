---
layout: post
title: "[CSS] Holy Grail Layout"
date: 2017-06-27
tags: [CSS, layout]
excerpt: "Holy Grail Layout 만들기"
comments: true
---

Holy Grail Layout: 성배를 찾는 것만큼 구성하기 힘들었던 레이아웃이다.
{: .notice}

# float를 이용해서

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        *{
            box-sizing: border-box;
        }
        .container {
            width: 540px;
            border: 1px solid gray;
            margin: auto;
        }
        header {
            border-bottom: 1px solid gray;
        }
        nav {
            float: left;
            width: 120px;
            border-right: 1px solid gray;
        }
        article {
            float: left;
            width: 300px;
            border-left: 1px solid gray;
            border-right: 1px solid gray;
            margin-left: -1px;
        }
        aside {
            float: left;
            width: 120px;
            border-left: 1px solid gray;
            margin-left: -1px;
        }
        footer {
            clear: both;
            border-top: 1px solid gray;
            text-align: center;
            padding: 20px;
        }
    </style>
</head>
<body>
  <div class="container">
      <header>
       <h1>CSS</h1>
   </header>
      <nav>
     <ul>
        <li>position</li>
        <li>float</li>
        <li>flex</li>
    </ul>  
   </nav>
      <article>
       <h2>float</h2>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur odit temporibus, repellat facilis beatae, commodi perferendis sit illum corporis ratione culpa nemo officia maxime! Consectetur nam consequatur deleniti, quas natus reiciendis, repudiandae earum placeat dolorem officiis? Ex quos doloremque ipsum odit consectetur, voluptatum eius, incidunt adipisci corporis. Rerum, sapiente, error!
   </article>
      <aside>
       ad
       </aside>
       <footer>
       copyleft
   </footer>
  </div>
</body>
</html>
```
- float를 사용할 때 container의 크기 조정: `box-sizing`을 이용
- border가 겹칠 때는 둘 다 주고 한 쪽에 `margin-left=-1px`

# flex
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        body {
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .container {
            display: flex;
            flex-direction: column;
            width: 800px;
            border: 1px solid gray;
        }
        header {
            border-bottom: 1px solid gray;
            padding-left:  20px;
        }
        footer {
            border-top: 1px solid gray;
            padding: 20px;
            text-align: center;
        }
        .content {
            display: flex;
        }
        .content nav {
            border-right: 1px solid gray;
        }
        .content aside {
            border-left: 1px solid gray;
        }
        nav, aside {
            flex-basis: 150px;
            flex-shrink: 0;
        }
        main {
            padding: 10px;
        }
        nav {
            order: -1;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>flex</h1>
        </header>
        <section class="content">
           <main>
                Lorem ipsum dolor sit amet, consectetur adipisicing elit. Accusantium ipsum dolorum consectetur magni mollitia dolorem vel eum alias sunt repudiandae voluptates inventore cumque ut eos, debitis eaque architecto dignissimos recusandae doloremque asperiores molestiae. Magnam in quis necessitatibus a provident, unde illo excepturi illum ullam autem esse, magni quia ipsa odio aperiam asperiores hic obcaecati dicta placeat amet. Numquam voluptatibus dolor dignissimos libero ex quibusdam enim deleniti unde sapiente dolorem deserunt labore totam ipsa laudantium, praesentium ullam d
                <p>
                    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Deleniti, sint. Fugiat nisi, eius adipisci! Voluptatem nihil voluptate laborum sit, labore debitis voluptatum nulla ipsum eius. Beatae ullam, sunt! Pariatur aperiam dolorem, quibusdam laborum dignissimos a recusandae voluptate quae fuga expedita soluta debitis possimus autem adipisci repellendus ullam veniam qui asperiores quas sapiente. Optio at, ea molestias incidunt totam quasi necessitatibus quaerat autem itaque assumenda eum error rem laborum dolorum pariatur blanditiis provident
                </p>
            </main>
            <nav>
                <ul>
                    <li>html</li>
                    <li>css</li>
                    <li>javascript</li>
                </ul>
            </nav>
            <aside>
                ad
            </aside>
        </section>
        <footer>
            <a href="https://absddsfdd.cooc.kr">홈페이지</a>
        </footer>
    </div>
</body>
</html>
```
- 아이템과 아이템을 담을 container가 필요하다.
- 컨테이너의 속성에 `display: flex`  
- `flex-basis`: 크기
- `flex-grow`: 아이템들이 나눠 갖는 비율
- `flex-shrink`: 화면이 작아질 때 줄어드는 비율
- `flex-direction`: 컨테이너 방향
- `flex-wrap`: 아이템 크기가 컨테이너 크기 보다 크면 줄바꿈
- `align-items`: 수직 정렬
- `justify-items`: 수평 정렬
- `align-content`: 아이템을 그룹핑
- `align-self`: 특정 아이템만 다르게 정렬

# 결론

- holy grail layout 구성할 때는 flex가 훨씬 쉽다! 그런데 학교 선배는 float를 가르쳐줬었다... 실제로는 float를 많이 사용하는 듯
