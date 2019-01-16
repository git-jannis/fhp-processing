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
- [Video or GIF here]

This sketch marks the first project of the class. It generates patterns, smiliar to those seen on the artwork »Untitled« by the artist and visual pioneer Vera Molnár. By clicking and moving the mouse, rectangles are generated on restricted but random x and y coordinates. 

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