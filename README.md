<!DOCTYPE html> <html lang="zh"> <head>
<meta charset="UTF-8" />
<title>跳转中...</title>
<meta name="viewport" content="width=device-width, initial-scale=1" /> <script>
// 所有 WhatsApp 链接 const links = [
"https://wa.me/447544108899",
"https://wa.me/447955572069", 
];
const LOCAL_KEY = "waAssignedIndex";
function getAssignedIndex() {
let saved = localStorage.getItem(LOCAL_KEY); if (saved !== null) {
return parseInt(saved, 10); }
const params = new URLSearchParams(window.location.search); const testIndex = parseInt(params.get("test"), 10);
if (!isNaN(testIndex) && testIndex >= 0 && testIndex < links.length) {
localStorage.setItem(LOCAL_KEY, testIndex);
return testIndex; }
const randomIndex = Math.floor(Math.random() * links.length); localStorage.setItem(LOCAL_KEY, randomIndex);
return randomIndex;
}
function redirect() {
const index = getAssignedIndex(); const target = links[index]; window.location.href = target;
}

 window.onload = redirect; </script>
</head> <body> </body> </html> 
