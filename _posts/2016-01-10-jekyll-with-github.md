---
layout: post
title: jekyll+github로 블로그 시작하기
description: "jekyll을 통해 블로그를 만들고 github page에 호스팅하는 방법을 설명"
tags: [blog, gitgub, jekyll]
---
<html>
<head>
	<title>맥에서 jekyll과 github로 블로그 시작하기</title>
</head>
<body>
<h1>과정 요약</h1>
<p>블로그 설치 과정은 다음과 같다. 터미널을 통해 jekyll을 설치하고, github에 <code>blog</code>라는 이름으로 repository를 만들고 블로그 내용을 올리게 될 것이다. 생성된 repository 주소는 <code>https://github.com/사용자명/blog.git</code>이 되고, 이 과정에서 생성되는 블로그의 주소는 <code>http://사용자명.github.io/blog</code>가 된다.</p>

<h1>터미널을 통한 jekyll 설치</h1>
<p>
참고로 OS X에서 터미널을 이용해 jekyll 툴을 원활히 사용하기 위해서는 사전에 Xcode와 커멘트라인 툴이 설치되어 있어야 한다. jekyll는 다음의 명령으로 설치한다.</p>
<p>
<code>[sudoe] gem install jekyll</code>
</p>

<h1>프로젝트 주소 페이지 방식으로 블로그 생성</h1>
<p>
<div class="highlight">
<pre><code class="language-text" data-lang="text">jekyll new blog
cd blog
jekyll serve --watch</code></pre></div>
<code>jekyll new blog</code>현재 디록토리 밑에 blog 디렉토리를 만들고 jeckyll 기본 디렉토리와 파일을 생성한다. jeckyll은 기본적으로 서버를 내장하고 있어 NgineX와 같은 별도의 웹서버를 띄우지 않아도 만들어진 사이트를 확인할 수 있다. <code>jekyll serve --watch</code>를 실행하면 <code>localhost:4000</code>에서 로컬에 생성된 디폴트 jekyll 페이지를 볼 수 있다.
<br><code>--watch</code> 옵션은 사이트를 변경하는 대로 다시 빌드하여 브라우저에서 변경사항을 바로 확인할 수 있게하는 옵션이다.
</p>
<p>
<div class="highlight"><pre><code class="language-text" data-lang="text">git init
git checkout --orphan gh-pages
git remote add origin 저장소url
git add .
git commit -m &quot;Initialize blog&quot;
git push origin gh-pages  // 반드시 gh-pages 브랜치로 푸시해야 깃허브가 블로그 페이지를 만들어 준다.
</code></pre></div>
이제 <code>사용자명.github.io/blog</code>의 주소로 이동하면 자신의 블로그를 볼 수 있다. 참고로 동기화과정이 조금 오래 걸릴 수 있음을 인지하자.
</p>
<h1>블로그 포스팅</h1>
<p>jekyll은 각 블로그 글마다 파일이 따로 구성되어있다. 즉, jekyll이 각각의 파일을 보여주는 것이다. 그러므로 글을 등록하기 위해서는 로컬 디렉토리에 포스팅하고자 할 내용을 파일로 저장하고 <code>_post</code>폴더에 저장해야 한다. jekyll은 <code>_post</code>폴더에 있는 파일만 블로그 포스트로 인식한다.</p>
<p>블로그 포스트 파일명은 <code>YYYY-MM-DD-post-name.확장자</code> 형식으로 지정되어야 한다. 마크다운으로 작성된 경우 <code>YYYY-MM-DD-포스트이름.md</code>로 저장하면 된다. 또한 블로그 포스트는 항상 파일 앞에 <code>front matter</code>를 적어야 한다. jekyll는 front matter 블록으로 시작되는 파일만 처리한다. 각 front matter에는 "title"과 "layout" 필드는 반드시 들어가야 한다.</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">---
title: [제목]
layout: post
---

글 내용
</code></pre></div>
<p>이처럼 jekyll과 github 를 이용해서 무료로 기본적인 블로그를 하나 만들어 시작해볼 수 있었다.</p>
<h2>참고</h2>
<ul>
	<li><mark><a href="http://svperstarz.github.io/jekyll-docs-ko/">지킬 공식 사이트 한글 번역</a></mark></li>
</ul>
</body>
</html>