var ants=[]
var food=[]
var hive=100

function setup() {
	createCanvas(windowWidth, windowHeight);
	background(255);
	fill('red');
	ellipse(windowWidth/2, windowHeight/2, 10, 10);
	
	for (let i = 0; i < 20; i++) {
		noStroke();
		fill('yellow');
		food.push([random(windowWidth*0.25,windowWidth*0.75),random(windowHeight*0.25,windowHeight*0.75),random(0,20)])
		ellipse(food[i][0],food[i][1],food[i][2],food[i][2]);
	}
	
	for (let i = 0; i < 1000; i++) {
		ants.push(new Ant())
	}
}

function draw() {
	for (let i = 0; i < ants.length; i++) {
		ants[i].move()
	}
	showfood()
	fill('red');
	ellipse(windowWidth/2, windowHeight/2, Math.pow(hive,1/2), Math.pow(hive,1/2));
}

function showfood() {
	for (let i = food.length-1; i>=0; i-=1) {
		if (food[i][2]<0){
			food.splice(i,1)
			noStroke();
			fill('yellow');
			food.push([random(windowWidth*0.25,windowWidth*0.75),random(windowHeight*0.25,windowHeight*0.75),random(0,20)])
			ellipse(food[i][0],food[i][1],food[i][2],food[i][2]);
		} else {
			fill('yellow');
			ellipse(food[i][0],food[i][1],food[i][2],food[i][2]);
		}
	}
}






class Ant {
  constructor() {
    this.x = windowWidth/2;
    this.y = windowHeight/2;
    this.speed = 10;
    this.color = color('green');
		this.memory= [];
		this.food=0
  }

  move() {
		noStroke();
		fill('light grey');
		ellipse(this.x, this.y, 2.5, 2.5);
		if (this.food==0.5 && Math.pow(this.x-windowWidth/2,2)+Math.pow(this.y-windowHeight/2,2)<100) {
			this.food=0
			hive+=0.5
			
		}
		
		
		for (let i = 0; i < food.length; i++) {
			if (Math.pow(this.x-food[i][0],2)+Math.pow(this.y-food[i][1],2)<100){
				this.memory=[food[i][0],food[i][1]];
				if (this.food==0){
					this.food+=0.5
					this.color=color('red')
					fill('white');
					ellipse(food[i][0],food[i][1],food[i][2]+0.5,food[i][2]+0.5);
					food[i][2]-=0.5
					fill('yellow');
					ellipse(food[i][0],food[i][1],food[i][2],food[i][2]);
					
				}
			}
		}
		if (Math.pow(this.x-this.memory[0],2)+Math.pow(this.y-this.memory[1],2)<50 && this.food==0){
			this.memory=[]
			this.color=color('green')
		}
		
		
		if (this.memory.length==[]){
			if (Math.pow(this.x-windowWidth/2,2)+Math.pow(this.y-windowHeight/2,2)!=0) 
			{
				var xbias=(this.x-windowWidth/2)/pow(Math.pow(this.x-windowWidth/2,2)+Math.pow(this.y-windowHeight/2,2),1/2)
				var ybias=(this.y-windowHeight/2)/pow(Math.pow(this.x-windowWidth/2,2)+Math.pow(this.y-windowHeight/2,2),1/2)
			} else {
				var xbias=0
				var ybias=0
			}

			this.x += random(-this.speed, this.speed)-(pow(Math.pow(this.x-windowWidth/2,2)+Math.pow(this.y-windowHeight/2,2),1/2))*xbias/1000;
			this.y += random(-this.speed, this.speed)-(pow(Math.pow(this.x-windowWidth/2,2)+Math.pow(this.y-windowHeight/2,2),1/2))*ybias/1000;
			
		} else{
			if (this.food==0){
				var xbias=(this.x-this.memory[0])/pow(Math.pow(this.x-this.memory[0],2)+Math.pow(this.y-this.memory[1],2),1/2)
				var ybias=(this.y-this.memory[1])/pow(Math.pow(this.x-this.memory[0],2)+Math.pow(this.y-this.memory[1],2),1/2)
			} else {
				var xbias=(this.x-windowWidth/2)/pow(Math.pow(this.x-windowWidth/2,2)+Math.pow(this.y-windowHeight/2,2),1/2)
				var ybias=(this.y-windowHeight/2)/pow(Math.pow(this.x-windowWidth/2,2)+Math.pow(this.y-windowHeight/2,2),1/2)
			}
			this.x += random(-this.speed/5, this.speed/5)-this.speed*xbias/2;
			this.y += random(-this.speed/5, this.speed/5)-this.speed*ybias/2;
		}
		noStroke();
		fill(this.color);
		ellipse(this.x, this.y, 2, 2);
		
  }
}
