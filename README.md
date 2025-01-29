# IMGD-02

This is a dynamic and cool sunglasses case. Those lenses are dynamic.

# Instructions
1. set up canvas
2. set up color
3. Drawing the shape
4. Drawing the sunglasses
5. Set up dynamic effects
6. Drawing the mouth
7. Set up text effects

# Code 



function setup() {
    createCanvas(200, 200);
    noStroke();
    angleMode(DEGREES);
}

function draw() {
    background(180, 220, 240);
    
    // Coloring
    const fur = [245, 207, 160];  
    const shades = [40, 40, 60];  
    const frame = [180, 180, 180]; 
    const glare = [255, 255, 255, 150]; 

    const unit = 14; 
    const centerX = width/2 - unit*3.5;
    const centerY = height/2 - unit*3;

    // Drawing the shape
    fill(fur);
    beginShape();
    vertex(centerX + unit*2, centerY);
    bezierVertex(
        centerX, centerY - unit*2,
        centerX + unit*7, centerY - unit*2,
        centerX + unit*5, centerY
    );
    for(let y=0; y<7; y++){
        const w = 5 - abs(y-3);
        rect(centerX + (3 - w/2)*unit, centerY + y*unit, w*unit, unit);
    }
    endShape();

  
    fill(shades);
    // Left lens
    rect(centerX + unit, centerY + unit*2, unit*3, unit*2, 5);
    // Right lens
    rect(centerX + unit*4, centerY + unit*2, unit*3, unit*2, 5);
    fill(frame);
    rect(centerX + unit*3.3, centerY + unit*2.5, unit*1.4, unit/2);

  
    fill(glare);
    const glareX = map(sin(frameCount*3), -1, 1, 0, unit*2.5);
    rect(
        centerX + unit + glareX, 
        centerY + unit*2.5, 
        unit, 
        unit/2, 
        0, 5, 5, 0
    );
    rect(
        centerX + unit*4 + glareX, 
        centerY + unit*2.5, 
        unit, 
        unit/2, 
        0, 5, 5, 0
    );

   
    push();
    translate(centerX, centerY + unit*3);
    rotate(sin(frameCount*2)*2);
    fill(frame);
    rect(-unit*0.5, 0, unit*2, unit/3);
    pop();

    push();
    translate(centerX + unit*7, centerY + unit*3);
    rotate(-sin(frameCount*2)*2);
    fill(frame);
    rect(-unit*1.5, 0, unit*2, unit/3);
    pop();

  
    fill(255, 160, 160);
    beginShape();
    vertex(centerX + unit*2.5, centerY + unit*5);
    vertex(centerX + unit*4.5, centerY + unit*5);
    vertex(centerX + unit*4, centerY + unit*6);
    vertex(centerX + unit*3, centerY + unit*6);
    endShape(CLOSE);

    // Text 
    if(frameCount % 120 < 60){
        fill(255, 255, 255, 200);
        rect(width - unit*4, unit, unit*3, unit*2, 5);
        fill(0);
        textSize(unit);
        text("COOL", width - unit*3.5, unit*2.5);
    }
}

The link to the code: https://editor.p5js.org/zx1998120/sketches/RfT4noYml
