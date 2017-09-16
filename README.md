# KKRONSOL

Experiemental creation of basic 2d graphic game using HTML, CSS, JavaScript (Plain)
Game uses pure nature of prototype objects to render controls. 
Movement is possible using loops, device detection & enviroment.

#KKRONSOL Evolution


# 2ds Character.js

 /*global screen size*/
            var MIN_SCREEN_WIDTH = 0; 
            var MAX_SCREEN_WIDTH = window.innerWidth; 
            /*char constructor*/
            function Character(){}
            /*proto*/
            Character.prototype = {};
            
            /*apply proto glue*/
            Character.apply(Character.prototype,[]);
            
        
            Character.prototype = {
	      walk_min:0,
	      walk_max:6,
	      lu: document.querySelector("#lu"),
	      createChar: function(){
	        /*create our character*/
		c = document.createElement("img");
		p = "char/";
		ext = ".png";
		c.height = 100;
		c.id = "lu";
		c.className = "lu";
		c.src = p + this.walk_min + ext;
		document.querySelector(".set").appendChild(c);
		
		return c;
	      },
	      moveRight: function(l_value){
	        /*set prop config */
		this.lu = document.querySelector("#lu");
		/*config set direction*/
		px_pos = "position:fixed !important;left:";
		px_set = l_value;
		px_ext = "px";
		/*move set init values*/
		modProp = px_pos+ px_set + px_ext;
		/*mod attr in dom*/
		this.lu.setAttribute("style", modProp); 
		/*my ref*/
		//console.log(this.lu);
		/*step*/
		this.moveMotion(this.walk_min);
	      },
	      moveMotion: function(walker){
	        this.walk_min = this.walk_min;
	        if(this.walk_min < 5){
	          this.lu.src = "char/"+ this.walk_min +".png";
		 // console.log(this.walk_min);
		   this.walk_min = this.walk_min + 1;
		}else{
		   this.walk_min = 1;
		}
	      }
	 
            }
            
            
	    /*create new player*/
            Character.prototype.createChar();
            
            /*set char instruct move right 30 cm*/
      	    Character.prototype.moveRight(15);
      	    
      	    /*attach right button*/

            document.querySelector("#move-right").onclick = forward;
            document.querySelector("#move-stop").onclick = rewind;
            
            function forward(){
              /*move char forward to screen max innerWidth*/
		if(MIN_SCREEN_WIDTH < MAX_SCREEN_WIDTH !== 0){
		  MIN_SCREEN_WIDTH = MIN_SCREEN_WIDTH + 35;
		  
		  if(MIN_SCREEN_WIDTH > MAX_SCREEN_WIDTH == true){
		      MIN_SCREEN_WIDTH = MAX_SCREEN_WIDTH - 70;
		  }
		  Character.prototype.moveRight(MIN_SCREEN_WIDTH);
		  /*check if the minium init start point 
		    is equal to char movement when it reaches end point
		  */
		  
		  //console.log(MIN_SCREEN_WIDTH > MAX_SCREEN_WIDTH == false );
		   //console.log(MAX_SCREEN_WIDTH );
		  return MIN_SCREEN_WIDTH;
		}else{
		  MIN_SCREEN_WIDTH = MAX_SCREEN_WIDTH;
		  
		}
             }
            /*move char back to screen min_innerWidth */
             function rewind(){
                //console.log(Character.prototype.walk_min);
		if(MIN_SCREEN_WIDTH < MAX_SCREEN_WIDTH){
		  MIN_SCREEN_WIDTH = MIN_SCREEN_WIDTH - 35;
		   /*check if char has not reach screen bound for negatives*/
		    if(MIN_SCREEN_WIDTH - 35 < 0 == true){
		      MIN_SCREEN_WIDTH = 1;
		    }
		  /*move back _proto_*/
		  Character.prototype.moveRight(MIN_SCREEN_WIDTH);
		  return MIN_SCREEN_WIDTH;
		}else{
		  MIN_SCREEN_WIDTH = 0;
		  
		}
             }
            
            
            
