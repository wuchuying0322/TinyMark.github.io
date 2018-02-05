---
title: Welcome!
date: 2016-10-28
---
<div id="time"></div>
[主页](/)
[分类](/categories/)
[归档](/archives/)
[标签](/tag/)
<!-- [关于](/about/) -->

My [GitHub](https://github.com/TinyMark)

<script>
; ~function (dom) {
var date;
function formatT(str) {
return String(str).length == 2 ? str : String('0' + str)
};
setInterval(function () {
date = new Date();
dom.innerHTML = `${date.getFullYear()}-${date.getMonth() + 1}-${date.getDate()} ${formatT(date.getHours())}:${formatT(date.getMinutes())}:${formatT(date.getSeconds())}`;
}, 1000)
}(document.querySelector('#time'))
</script>
