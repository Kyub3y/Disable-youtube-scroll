// ==UserScript==
// @name         Disable Fullscreen Scrolling on YouTube
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Disables scrolling while fullscreen on YouTube
// @author       You
// @match        https://*.youtube.com/*
// @match        http://*.youtube.com/*
// @grant        none
// @require http://code.jquery.com/jquery-latest.js
// ==/UserScript==

if (window.top === window.self) { addJsNode(main) }

function main() {
    var setScrollEventsValue = (v) => {
        window.onwheel = window.onmousewheel = document.onmousewheel = v;
    }
    document.addEventListener("fullscreenchange", () => {
        var disableScrollHandler = (e) => {
            e = e || window.event;
            if (e.preventDefault) { e.preventDefault(); }
            e.returnValue = false;
        }
        if (document.fullscreen || document.webkitIsFullScreen) {
            setScrollEventsValue(disableScrollHandler)
        } else {
            setScrollEventsValue(null);
        }
    });
}

function addJsNode(func) {
  const scriptNode = document.createElement('script')
  scriptNode.type = 'text/javascript'
  scriptNode.textContent = '('+func.toString()+')()'

  const target = document.getElementsByTagName('head')[0] ||
                  document.body || document.documentElement
  target.appendChild(scriptNode)
}
