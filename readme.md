# Task
Select at least 3 sketches that you made this semester (or some new ones) and put them online in at least one of these sites:

As a Bitbucket.com or Github.com Repository
Website (if you already have one or make one with glitch.com for free) https://glitch.com/culture/website-starter-kit/
As an Incom Project page
Each sketch should have:

a description of what the code is about
an image, or a gif, or a video, or an embedded P5.js sketch
you should also include the code of your sketch
Post your documentation link to our incom https://fhp.incom.org/workspace/7990/files Documentation Links
with this linkname: Documentation_MaxiMuster

Your documentation Link must be in incom by the next class
Please select three activities from this list in your row for the next class




## Sketch 1 — Hommage to Vera Molnár’s »Untitled«
![Animation of Supershape Sketch](/img/molnar.gif)

🌀 This sketch marks the first project of the class. It generates patterns, smiliar to those seen on the artwork »Untitled« by the artist and visual pioneer Vera Molnár. By clicking and moving the mouse, rectangles are generated on restricted but random x and y coordinates. 

	import processing.pdf.*; // imports PDF library for exporting screenshots

	void setup() {
	  size(1024, 750);
	  frameRate(20); // controls the frequency of rectangles drawn
	  background(240, 240, 235); 
	  //pixelDensity(displayDensity()); // retina res. doesnt workt with PDF export
	  beginRecord(PDF, "hommage-" + year() + "-" + month() + "-" + day() + "--" + hour() + "h." + minute() + "m." + second() + ".pdf"); // starts "recording"
	}

	void draw() {
	  if (mousePressed && (mouseButton == LEFT)) {  // draws rectangles on left click
		stroke(200, 50, 30);
		strokeWeight(2);
		noFill();
		rect(mouseX, mouseY, 30, 300);
		rect(mouseX+random(5, 10), mouseY+random(5, 10), 30, 300);
	  } else if (mousePressed && (mouseButton == RIGHT)) {
		background(240, 240, 235); // resets canvas to bg color
	  } else { // makes sure to leave no trail
		noStroke(); 
		noFill();
	  }
	}

	void keyTyped() { // quits recording once a random key is pressed
	  endRecord();
	}

🔗 Download the sketch file here: ![Molnar Sketch file](sketch_files/molnar_sketch.zip)





## Sketch 2 — Supershapes build with sin and cos functions
![Animation of Supershape Sketch](/img/supershape.gif)
🌀 Text here

		import processing.pdf.*;
		boolean record;
		float t;

		void setup() {
			size(500, 500);
			beginRecord(PDF, "everything-###.pdf");
		}

		void draw() {
			stroke(0);
			strokeWeight(5);
			translate(width/2, height/3);
			point(x(t), y(t));
			t++;
		}

		void keyPressed() {
			if (key == 'q') {
				endRecord();
				exit();
			}
		}

		float x(float t) {
			return sin(t/8) * 100 + sin(t/6)*100; // freq=sin(t/8), amplitude=*100)
		}

		float y(float t) {
			return cos(t/4) * 100 + cos(t/2)*25;
		}


## Sketch 3 — Wildlife (Object Oriented Programming)
![Animation of Supershape Sketch](/img/wildlife.gif)
🌀 Text here

		Worm[] worms = new Worm[10]; // declare array + create list of 10 spots

		void setup() {
		size(800, 800, P2D);
		smooth(8); // antialiasing
			for (int i = 0; i < worms.length; i++) {
				worms[i] = new Worm(i*10, i*100, random(3, 5));
			}
		}

		void draw() {
			background(50, 150, 80);
			for (int i = 0; i < worms.length; i++) {
				worms[i].display();
				worms[i].move();
				worms[i].finish();
			}
		}

		class Worm {
		float wormX;
		float wormY;
		float wormHeight;
		float wormLength;
		float legLength;
		float legSpacing;
		float wormSpeed;

		Worm(float passingOverX, float passingOverY, float passingOverSpeed) {
			wormX = passingOverX;
			wormY = passingOverY;
			wormHeight = random(30,60);
			wormLength = random(100,200);
			legLength = random(5,10);
			legSpacing = wormLength/legLength;
			wormSpeed = passingOverSpeed;
		}

		void move() {
			wormX = wormX+wormSpeed;
		}

		void finish() {
			if (wormX > width) {
				wormX = 0-wormLength;
				}
		}

		void display() {
			// body
			fill(255);
			rect(wormX, wormY, wormLength, wormHeight); // x y w h corner

			// eye
			stroke(0);
			fill(255);
			ellipse(wormX+wormLength/1.1, wormY+wormHeight/3, 10, 10);

			// legs
			stroke(255);
				for (float i = wormX; i < wormX+wormLength; i = i + legSpacing) {
					line(i, wormY+wormHeight, i, wormY+wormHeight+legLength+random(10, 20)); // x1 y1 - x2 y2
				}
			}
		}
