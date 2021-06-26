# **Markdown **

## **목차**

- [Virutal Code 환경 설정](#virutal-code-환경-설정)
- [Markdown HTML 변환하기](#markdown-html-변환하기)
- [Markdown to HTML Javascript 라이브러리](#markdown-to-html-javascript-라이브러리)
- [참조 사이트](#참조-사이트)

## **Virutal Code 환경 설정**

1. Virtual Studio Code 다운로드

   - https://code.visualstudio.com

2. Virutal Studio Plugin 설치
   - markdownlint - David Anson
   - Markdown Theme Kit ms-vscode
   - Markdown Shortcuts - mdickin
   - Image preview - Kiss Tamas
   - vscode-pdf - tomoki1207
   - Markdown PDF - yzane

## **Markdown HTML 변환하기**

1. NodeJS 설치

   - https://nodejs.org/ko

2. 전역 markdown-it Package 설치

   - npm install -g markdown-it

3. 변환 폴더 이동 후 명령어 실행
   - markdown-it "파일명".md -o index.html

## **Markdown to HTML Javascript 라이브러리**

1. showdown: 28KB. Basically the gold standard; it is the basis for pagedown.

2. pagedown: 8KB. This is what powers StackExchange, so you can see for yourself which features it supports (it is very robust but missing tables, definition lists, footnotes, etc). In addition to the 8KB converter script, it also offers editor and sanitizer scripts, both of which StackExchange also uses.

3. drawdown: 1.3KB. Full disclosure, I wrote it. Broader feature scope than any other lightweight converter; handles most but not all of the CommonMark spec. Not recommended for user editing but very useful for presenting information in web apps. No inline HTML.

4. markdown-it: 104KB. Follows the CommonMark spec; supports syntax extensions; produces secure output by default. Fast; may actually be as robust as showdown, but very large. Is the basis for http://dillinger.io/.

5. marked: 19KB. Comprehensive; tested against unit test suite; supports custom lexer rules.

6. micromarkdown: 5KB. Supports a lot of features, but is missing some common ones like unordered lists using \* and some common ones that aren't strictly part of the spec like fenced code blocks. Many bugs, throws exceptions on most longer documents. I consider it experimental.

7. nano-markdown: 1.9KB. Feature scope limited to things used by most documents; more robust than micromarkdown but not perfect; uses its own very basic unit test. Reasonably robust but breaks on many edge cases.

8. mmd.js: 800 bytes. The result of an effort to make the smallest possible parser that is still functional. Supports a small subset; document needs to be tailored for it.

9. markdown-js: 54KB (not available for download minified; would probably minify to ~20KB). Looks pretty comprehensive and includes tests, but I'm not very familiar with it.

10. meltdown: 41KB (not available for download minified; would probably minify to ~15KB). jQuery plugin; Markdown Extra (tables, definition lists, footnotes).

11. unified.js: varies, 5-100KB. A plugin-based system for converting between html, markdown, and prose. Depending on what plugins you need (spell-checking, syntax-highlightin

## **참조 사이트**

- https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4
- https://code.visualstudio.com/docs/languages/markdown#_compiling-markdown-into-html
- https://www.markdowntutorial.com/
