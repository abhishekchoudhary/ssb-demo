---
title: Writing room
slug: writing-room
description: Ten quiet minutes. A blank page. A beginning.
draft: false
publishedSlug: writing-room
tags:
  - writing
  - tools
format: html
showHeader: true
showFooter: false
---
<!doctype html>
<html lang="en"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1"><title>Writing room</title>
<style>
*{box-sizing:border-box}body{margin:0;background:#f8f8f3;color:#282c27;font:16px/1.6 system-ui,sans-serif}main{max-width:880px;margin:auto;padding:36px 24px}h1{font:normal clamp(38px,7vw,58px)/1.1 Georgia,serif;letter-spacing:-1.5px;margin:12px 0}.eyebrow{font-size:11px;letter-spacing:2px;text-transform:uppercase;color:#666c61}.intro{color:#666c61;margin-bottom:26px}.controls{display:flex;gap:10px;align-items:center;flex-wrap:wrap;padding:18px 0;border-top:1px solid #d9ddd2;border-bottom:1px solid #d9ddd2}button,select{font:inherit;padding:8px 14px;border:1px solid #b8c4b4;border-radius:4px;background:transparent;color:inherit}button{cursor:pointer}button:first-of-type{background:#355541;color:white}label{font-size:13px}output{font:24px ui-monospace,monospace;min-width:90px;margin-left:auto}textarea{display:block;width:100%;min-height:330px;resize:vertical;margin:24px 0 12px;padding:24px;background:#fffffb;border:1px solid #d9ddd2;border-radius:6px;color:inherit;font:20px/1.8 Georgia,serif}.below{display:flex;justify-content:space-between;gap:16px;flex-wrap:wrap;color:#666c61;font-size:13px}button:focus-visible,select:focus-visible,textarea:focus-visible{outline:3px solid #67876e;outline-offset:3px}#status{min-height:26px;color:#355541}.prompt{padding:16px;background:#edf0e7;border-radius:4px}noscript{color:#875332}@media(max-width:500px){main{padding:24px 18px}textarea{padding:16px;font-size:18px}output{margin-left:0}}
</style></head><body><main>
<p class="eyebrow">A little experiment</p><h1>Writing room</h1><p class="intro">Pick a few minutes. Write what comes. Keep what you like.</p>
<p class="prompt"><strong>Today's prompt:</strong> Describe a place using only the things you noticed.</p>
<div class="controls"><label for="minutes">Minutes</label><select id="minutes"><option value="5">5</option><option value="10" selected>10</option><option value="25">25</option></select><button id="start" type="button">Start</button><button id="reset" type="button">Reset timer</button><output id="clock" aria-label="Time remaining">10:00</output></div>
<p id="status" role="status">Ready when you are.</p><label for="words">Your page</label><textarea id="words" placeholder="Start with one detail…"></textarea>
<div class="below"><span id="count">0 words</span><span>This page does not save your writing. Download it before leaving.</span></div><p><button id="download" type="button">Download writing</button></p>
<noscript>The timer and download need JavaScript. You can still write here and copy the text.</noscript>
</main><script>
const minutes=document.getElementById('minutes'),clock=document.getElementById('clock'),start=document.getElementById('start'),status=document.getElementById('status'),words=document.getElementById('words');
let left=600000,deadline=0,timer;
function draw(){const seconds=Math.ceil(left/1000);clock.textContent=String(Math.floor(seconds/60)).padStart(2,'0')+':'+String(seconds%60).padStart(2,'0');}
function stop(){clearInterval(timer);timer=undefined;minutes.disabled=false;start.textContent='Start';}
function tick(){left=Math.max(0,deadline-Date.now());draw();if(!left){stop();status.textContent='Time is yours again. Keep going, or save a few good lines.';}}
start.onclick=()=>{if(timer){left=Math.max(0,deadline-Date.now());stop();draw();status.textContent='Paused.';return;}if(!left)left=Number(minutes.value)*60000;deadline=Date.now()+left;minutes.disabled=true;start.textContent='Pause';status.textContent='One sentence at a time.';timer=setInterval(tick,250);words.focus();};
document.getElementById('reset').onclick=()=>{stop();left=Number(minutes.value)*60000;draw();status.textContent='Ready when you are. Your writing stays.';};minutes.onchange=()=>{left=Number(minutes.value)*60000;draw();};
words.oninput=()=>{const n=words.value.trim()?words.value.trim().split(/\s+/u).length:0;document.getElementById('count').textContent=n+' '+(n===1?'word':'words');};
document.getElementById('download').onclick=()=>{if(!words.value.trim()){status.textContent='Write something first.';return;}const url=URL.createObjectURL(new Blob([words.value],{type:'text/plain;charset=utf-8'}));const a=document.createElement('a');a.href=url;a.download='a-few-good-lines.txt';a.click();setTimeout(()=>URL.revokeObjectURL(url),1000);status.textContent='Downloaded. Keep a copy somewhere good.';};
</script></body></html>
