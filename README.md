# simple_car_game
<h3 align="center"> Classic Car Racing game using Vanilla JavaScript </h3>

  //document.querySelector('');
  //document.addEventListener('event',function);
  
  function keyDown(e){
      e.preventDefault();
      keys[e.key]=true;
  }
  function isCollide(a,b){
      aRect=a.getBoundingClientRect();
      bRect=b.getBoundingClientRect();
      return !((aRect.bottom<bRect.top)||(aRect.top>bRect.bottom)||(aRect.right<bRect.left)||(aRect.left>bRect.right))
  }
  function isCollide(a,b){
      aRect=a.getBoundingClientRect();
      bRect=b.getBoundingClientRect();
      return !((aRect.bottom<bRect.top)||(aRect.top>bRect.bottom)||(aRect.right<bRect.left)||(aRect.left>bRect.right))
  }
  function moveEnemy(car){
      let enemy=document.querySelectorAll('.enemy');
      enemy.forEach(function(item){

          if(isCollide(car,item)){
              console.log("Bang!");
              endGame();
          }
          if(item.y >=750){
              item.y=-300;
              item.style.left=Math.floor(Math.random()*350)+"px";
          }
          item.y+=player.speed;
          item.style.top=item.y+"px";
      })
  }
  function start(){
      //gameArea.classList.remove('hide');
      startScreen.classList.add('hide');
      gameArea.innerHTML="";
      player.start=true;
      player.score=0;
      window.requestAnimationFrame(gamePlay);

      for(x=0;x<5;x++){
          let roadLine=document.createElement('div');
          roadLine.setAttribute('class','lines');
          roadLine.y=(x*150);
          roadLine.style.top=roadLine.y+"px";
          gameArea.appendChild(roadLine);
      }

      let car=document.createElement('div');
      car.setAttribute('class','car');
      gameArea.appendChild(car);

      player.x=car.offsetLeft;
      player.y=car.offsetTop;

      for(x=0;x<3;x++){
          let enemyCar=document.createElement('div');
          enemyCar.setAttribute('class','enemy');
          enemyCar.y=((x+1)*350)*-1;
          enemyCar.style.top=enemyCar.y+"px";
          enemyCar.style.backgroundColor=randomColor();
          enemyCar.style.left=Math.floor(Math.random()*350)+"px";
          gameArea.appendChild(enemyCar);
      }
  }
```
:innocent:If you hit:boom: you loose...<br>

Created with :heart:
