```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>标题</title>
    <style type="text/css">
      /* ul,
      li {
        margin: 0;
        padding: 0;
        border: 0;
        font-size: 100%;
        font: inherit;
        vertical-align: baseline;
      } */
      ol,
      ul {
        list-style: none;
      }
      .box {
        width: 202px;
        height: 32px;
        line-height: 30px;
        margin: 100px auto;
        border: 1px solid #000;
        position: relative;
        overflow: hidden;
      }
      .box ul {
        width: 100%;
        height: 500%;
        position: absolute;
        top: 0;
        left: 0;
        margin: 0;
        animation: czlb 10s linear infinite;
      }
      .box ul li {
        margin: 0;
        width: 100%;
        height: 20%;
        padding-left: 10px;
      }
      @keyframes czlb {
        0% {
          top: 0;
        }
        10% {
          top: -100%;
        }
        25% {
          top: -100%;
        }
        35% {
          top: -200%;
        }
        50% {
          top: -200%;
        }
        65% {
          top: -300%;
        }
        75% {
          top: -300%;
        }
        85% {
          top: -400%;
        }
        100% {
          top: -400%;
        }
      }
    </style>
  </head>
  <body>
    <div class="box">
      <ul>
        <li>第1条公告...</li>
        <li>第2条公告...</li>
        <li>第3条公告...</li>
        <li>第4条公告...</li>
        <li>第5条公告...</li>
      </ul>
    </div>
  </body>
</html>


```