const player = new Plyr('#player',{
    settings: []
});

var video_player = document.getElementById("video_player"),
links        = video_player.getElementsByTagName('a');

for (var i=0; i<links.length; i++) {
links[i].onclick = handler;

}



function handler(e) {
e.preventDefault();
videotarget = this.getAttribute("href");
filename = videotarget.substr(0, videotarget.lastIndexOf('.')) || videotarget;
video = document.querySelector("#video_player video");
source = document.querySelectorAll("#video_player video source");
source[0].src = filename + ".m3u8";
localStorage.setItem('LavenganzadelajuanasT1-link', source[0].src);
video.autoplay = true;  
video.load();



texto = this.innerText;
localStorage.setItem('LavenganzadelajuanasT1-numero', texto);

cambiar = document.getElementById('titulo');
cambiar.innerText = texto;

localStorage.setItem('LavenganzadelajuanasT1LavenganzadelajuanasT1-actual', 0)
window.location.reload();

}



let numero = localStorage.getItem('LavenganzadelajuanasT1-numero');
document.getElementById('titulo').innerText = numero;


let link = localStorage.getItem('LavenganzadelajuanasT1-link');
let enlace = document.querySelectorAll("#video_player video source");
enlace[0].src = link;

window.scrollTo({ top: 0, behavior: 'smooth' }); 

function actualTime() {
var myPlayer = document.getElementById('player');

if (myPlayer.currentTime != 0){
    localStorage.setItem('LavenganzadelajuanasT1-actual', myPlayer.currentTime);
}

setTimeout(actualTime, 3000);    
}

actualTime();

let video = document.querySelector("#video_player video");
video.play();
document.getElementById('player').currentTime = localStorage.getItem('LavenganzadelajuanasT1-actual');



var boxes = document.querySelectorAll("input[type='checkbox']");
for (var i = 0; i < boxes.length; i++) {
    var box = boxes[i];
    if (box.hasAttribute("store")) {
        setupBox(box);
    }
}
function setupBox(box) {
    var storageId = box.getAttribute("store");
    var oldVal    = localStorage.getItem(storageId);
    box.checked = oldVal === "true" ? true : false;

    box.addEventListener("change", function() {
        localStorage.setItem(storageId, this.checked); 
    });
}
