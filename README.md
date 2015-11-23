
Table disenos;
PFont textos;
PFont headers;

//variables 2004
int resi4p, resi4c, nresi4p, nresi4c, tot4;
float rp4, rc4, nrp4, nrc4;
//variables 2005
int resi5p, resi5c, nresi5p, nresi5c, tot5;
float rp5, rc5, nrp5, nrc5;
//variables 2006
int resi6p, resi6c, nresi6p, nresi6c, tot6;
float rp6, rc6, nrp6, nrc6;
//variables 2007
int resi7p, resi7c, nresi7p, nresi7c, tot7;
float rp7, rc7, nrp7, nrc7;
//variables 2008
int resi8p, resi8c, nresi8p, nresi8c, tot8;
float rp8, rc8, nrp8, nrc8;
//variables 2009
int resi9p, resi9c, nresi9p, nresi9c, tot9;
float rp9, rc9, nrp9, nrc9;
//variables 2010
int resi10p, resi10c, nresi10p, nresi10c, tot10;
float rp10, rc10, nrp10, nrc10;
//variables 2011
int resi11p, resi11c, nresi11p, nresi11c, tot11;
float rp11, rc11, nrp11, nrc11;
//variables 2012
int resi12p, resi12c, nresi12p, nresi12c, tot12;
float rp12, rc12, nrp12, nrc12;
//variables 2013
int resi13p, resi13c, nresi13p, nresi13c, tottrece;
float rp13, rc13, nrp13, nrc13;
float degrees = 0.0;
float currentDegreesOfRotation = 0.0;
float nextDegrees = 0.0;
boolean needsToMove = false;


void setup() {
  size(1080, 720, P3D); 
  textos= loadFont("Comfortaa-Light-25.vlw"); 
  headers=loadFont("Georgia-100.vlw");

  smooth(5);
}

void draw() {

  disenos= loadTable("TABLA DISEÑOS INDUSTRIALES SIMPLIFICADA.csv", "header");  

  background(40);
  lights();

  //convenciones

  strokeWeight(10);
  textFont(textos, 15);
  
  fill(255);
  textAlign(LEFT, CENTER);

  stroke(255);//blanco
  line(750, 530, 800, 530);
  text("Presentados por Residentes", 810, 530);

  stroke(150); //GRIS CLARO
  line(750, 560, 800, 560);
  text("Concedidos a Residentes", 810, 560);
  
  stroke(100); //GRIS OSCURITO
  line(750, 590, 800, 590);
  text("Presentados por No Residentes", 810, 590);

  stroke(80); //GRIS OSCURO
  line(750, 620, 800, 620);
  text("Concedidos a No Residentes", 810, 620);



  //visor

  strokeJoin(ROUND);
  stroke(255, 60);
  strokeWeight(8);
  noFill();
  rect(200, 110, 500, 350);
  rect(215, 125, 470, 320);
  stroke(255);
  strokeWeight(20);
 

  fill(255);
  textFont(headers, 27);
  text("Diseños industriales ", 730, 210);
  text("presentados y concedidos", 730, 235);
  textFont(headers, 80);
  text("2004-13", 730, 130);



  for (int years=0; years<10; years++) {

    fill(255);
    textFont (textos, 20); 
    text(disenos.getInt(years, 0), 62, (years+2.1)*60);
  }

  //Interacción: if (boton del año) entonces rotateX (radians(angulo para 
  //que la esfera quede de frente) y aparece información sobre año y cantidades.

  interaccion();


  if (needsToMove == true) {
    if (currentDegreesOfRotation != nextDegrees) {        
      currentDegreesOfRotation -= 1;
      if (currentDegreesOfRotation < -360) {
        currentDegreesOfRotation = 0.0;
      }
    } else { 
      needsToMove = false;
      println("needs to move FALSE");
    }
  }

  rotateX(radians(currentDegreesOfRotation));

  //2004
  cuatro();

  //2005
  pushMatrix();
  rotateX(radians(36));
  cinco();
  popMatrix();

  //2006
  pushMatrix();
  rotateX(radians(72));
  seis();
  popMatrix();

  //2007
  pushMatrix();
  rotateX(radians(108));
  siete();
  popMatrix();

  //2008
  pushMatrix();
  rotateX(radians(144));
  ocho();
  popMatrix();

  //2009
  pushMatrix();
  rotateX(radians(180));
  nueve();
  popMatrix();

  //2010
  pushMatrix();
  rotateX(radians(216));
  diez();
  popMatrix();

  //2011
  pushMatrix();
  rotateX(radians(252));
  once();
  popMatrix();

  //2012
  pushMatrix();
  rotateX(radians(288));
  doce();
  popMatrix();

  //2013
  pushMatrix();
  rotateX(radians(324));
  trece();
  popMatrix();
}

void interaccion() {
  if (mouseY>75 && mouseY<135 && mouseX>40 && mouseX<140 && needsToMove ==false) {
    textFont (textos, 15);
    fill(255);
    text(resi4p, 476, 340);
    text(resi4c, 374, 360);
    text(nresi4p, 330, 240);
    text(nresi4c, 473, 223);

    noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
    fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(0,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(0,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(0,6)+disenos.getInt(0,3), 910+30,410);
    

    textFont(headers, 100);
    fill(255);
    text("2004", 750, 130);
  }
  if (mouseY>135 && mouseY<195 && mouseX>40 && mouseX<140 && needsToMove ==false) {
    textFont (textos, 15);
    fill(255);
    text(resi5p, 500, 333);
    text(resi5c, 393, 380);
    text(nresi5p, 310, 287);
    text(nresi5c, 467, 204);

   noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
    fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(1,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(1,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(1,6)+disenos.getInt(1,3), 910+30,410);
    

    textFont(headers, 100);
    fill(255);
    text("2005", 750, 130);
  }

  if (mouseY>195 && mouseY<255 && mouseX>40 && mouseX<140 && needsToMove ==false) {

    textFont (textos, 15);
    fill(255);
    text(resi6p, 494, 342);
    text(resi6c, 413, 384);
    text(nresi6p, 310, 277);
    text(nresi6c, 484, 218);

    noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
        fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(2,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(2,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(2,6)+disenos.getInt(2,3), 910+30,410);
    

    textFont(headers, 100);
    fill(255);
    text("2006", 750, 130);
  }

  if (mouseY>255 && mouseY<315 && mouseX>40 && mouseX<140 && needsToMove ==false) {
    textFont (textos, 15);
    fill(255);
    text(resi7p, 479, 346);
    text(resi7c, 380, 367);
    text(nresi7p, 315, 261);
    text(nresi7c, 485, 227);

    noStroke();
    fill(40);
    rect(730, 70, 320, 110);

    fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(3,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(3,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(3,6)+disenos.getInt(3,3), 910+30,410);

    textFont(headers, 100);
    fill(255);
    text("2007", 750, 130);
  }
  if (mouseY>315 && mouseY<375 && mouseX>40 && mouseX<140 && needsToMove ==false) {

    textFont (textos, 15);
    fill(255);
    text(resi8p, 515, 331);
    text(resi8c, 463, 385);
    text(nresi8p, 288, 279);
    text(nresi8c, 496, 207);

   noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
        fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(4,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(4,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(4,6)+disenos.getInt(4,3), 910+30,410);

    textFont(headers, 100);
    fill(255);
    text("2008", 750, 130);
    
  }
  if (mouseY>375 && mouseY<435 && mouseX>40 && mouseX<140 && needsToMove ==false) {

    textFont (textos, 15);
    fill(255);
    text(resi9p, 480, 346);
    text(resi9c, 436, 372);
    text(nresi9p, 322, 325);
    text(nresi9c, 464, 204);

   noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
        fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(5,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(5,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(5,6)+disenos.getInt(5,3), 910+30,410);

    textFont(headers, 100);
    fill(255);
    text("2009", 750, 130);
   
  }
  if (mouseY>435 && mouseY<495 && mouseX>40 && mouseX<140 && needsToMove ==false) {

    textFont (textos, 15);
    fill(255);
    text(resi10p, 495, 340);
    text(resi10c, 436, 380);
    text(nresi10p, 312, 325);
    text(nresi10c, 465, 197);

   noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
        fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(5,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(5,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(5,6)+disenos.getInt(5,3), 910+30,410);

    textFont(headers, 100);
    fill(255);
    text("2010", 750, 130);
  }
  if (mouseY>495 && mouseY<555 && mouseX>40 && mouseX<140 && needsToMove ==false) {

    textFont (textos, 15);
    fill(255);
    text(resi11p, 544, 352);
    text(resi11c, 385, 424);
    text(nresi11p, 257, 292);
    text(nresi11c, 521, 180);   

   noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
        fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(6,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(6,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(6,6)+disenos.getInt(6,3), 910+30,410);

    textFont(headers, 100);
    fill(255);
    text("2011", 750, 130);
  }
  if (mouseY>555 && mouseY<615 && mouseX>40 && mouseX<140 && needsToMove ==false) {

    textFont (textos, 15);
    fill(255);
    text(resi12p, 506, 365);
    text(resi12c, 350, 390);
    text(nresi12p, 291, 234);
    text(nresi12c, 510, 206);

    noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
        fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(7,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(7,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(7,6)+disenos.getInt(7,3), 910+30,410);

    textFont(headers, 100);
    fill(255);
    text("2012", 750, 130);
  }
  if (mouseY>615 && mouseY<675 && mouseX>40 && mouseX<140 && needsToMove ==false) {

    textFont (textos, 15);
    fill(255);
    text(resi13p, 517, 413);
    text(resi13c, 330, 427);
    text(nresi13p, 242, 248);
    text(nresi13c, 538, 178);

    noStroke();
    fill(40);
    rect(730, 70, 320, 110);
    
        fill(255);
    text("   Total presentados= ", 750+30, 350);
    text(disenos.getInt(8,3), 910+30,350);
    
    text("+ Total concedidos= ", 750+30, 380);
    text(disenos.getInt(8,6), 910+30,380);
    
    strokeWeight(1);
    stroke(255);
    line(750+30,395,945+30,395);
    
     text("   Total= ", 750+30, 410);
    text(disenos.getInt(8,6)+disenos.getInt(8,3), 910+30,410);

    textFont(headers, 100);
    fill(255);
    text("2013", 750, 130);
  }
}



//elementos 2004  

void cuatro() {

  tot4= disenos.getInt(0, 3)+disenos.getInt(0, 6);
  resi4p= disenos.getInt(0, 1);
  resi4c= disenos.getInt(0, 4);
  nresi4p= disenos.getInt(0, 2);
  nresi4c= disenos.getInt(0, 5);

  rp4=map(resi4p, 0, 595, 0, 360);
  rc4=map(resi4c, 0, 595, 0, 360);
  nrp4=map(nresi4p, 0, 595, 0, 360);
  nrc4=map(nresi4c, 0, 595, 0, 360);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);

  //arco residentes presentados 2004
  stroke(255); //BLANCO
  arc(0, 0, tot4, tot4, radians(0), radians(rp4) );
  //arco residentes concedidos 2004
  stroke(150); //GRIS CLARO
  arc(0, 0, tot4, tot4, radians(rp4), radians(rp4+rc4) );

  //arco no residentes presentados 2004
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot4, tot4, radians(rp4+rc4), radians(rp4+rc4+nrp4) );
  //arco no residentes concedidos 2004
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot4, tot4, radians(rp4+rc4+nrp4), radians(rp4+rc4+nrp4+nrc4) );


  //esfera total 2004 

  stroke(153, 197, 200);
  strokeWeight(0.3);
  fill(165, 209, 212);//PEACEFULLY
  sphere(tot4/2.5);
  popMatrix();
}

void cinco() {

  disenos= loadTable("TABLA DISEÑOS INDUSTRIALES SIMPLIFICADA.csv", "header");  

  tot5= disenos.getInt(1, 3)+disenos.getInt(1, 6);
  resi5p= disenos.getInt(1, 1);
  resi5c= disenos.getInt(1, 4);
  nresi5p= disenos.getInt(1, 2);
  nresi5c= disenos.getInt(1, 5);

  rp5=map(resi5p, 0, 705, 0, 360);
  rc5=map(resi5c, 0, 705, 0, 360);
  nrp5=map(nresi5p, 0, 705, 0, 360);
  nrc5=map(nresi5c, 0, 705, 0, 360);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 2005
  stroke(255); //BLANCO
  arc(0, 0, tot5, tot5, radians(0), radians(rp5) );
  //arco residentes concedidos 2005
  stroke(150); //GRIS CLARO
  arc(0, 0, tot5, tot5, radians(rp5), radians(rp5+rc5) );

  //arco no residentes presentados 2005
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot5, tot5, radians(rp5+rc5), radians(rp5+rc5+nrp5) );
  //arco no residentes concedidos 2005
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot5, tot5, radians(rp5+rc5+nrp5), radians(rp5+rc5+nrp5+nrc5) );


  //esfera total 2005 

  stroke(79-12, 192-12, 203-12);
  strokeWeight(0.3);
  fill(79, 192, 203);//BEIRAMAR
  sphere(tot5/2.5);
  popMatrix();
}

void seis() {

  disenos= loadTable("TABLA DISEÑOS INDUSTRIALES SIMPLIFICADA.csv", "header");  

  tot6= disenos.getInt(2, 3)+disenos.getInt(2, 6);
  resi6p= disenos.getInt(2, 1);
  resi6c= disenos.getInt(2, 4);
  nresi6p= disenos.getInt(2, 2);
  nresi6c= disenos.getInt(2, 5);

  rp6=map(resi6p, 0, 714, 0, 360);
  rc6=map(resi6c, 0, 714, 0, 360);
  nrp6=map(nresi6p, 0, 714, 0, 360);
  nrc6=map(nresi6c, 0, 714, 0, 360);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 2006
  stroke(255); //BLANCO
  arc(0, 0, tot6, tot6, radians(0), radians(rp6) );
  //arco residentes concedidos 2006
  stroke(150); //GRIS CLARO
  arc(0, 0, tot6, tot6, radians(rp6), radians(rp6+rc6) );

  //arco no residentes presentados 2006
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot6, tot6, radians(rp6+rc6), radians(rp6+rc6+nrp6) );
  //arco no residentes concedidos 2006
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot6, tot6, radians(rp6+rc6+nrp6), radians(rp6+rc6+nrp6+nrc6) );


  //esfera total 2006

 stroke(75-12, 141-12, 159-12);
  strokeWeight(0.3);
  fill(75, 141, 159);//DUSTY BLUE
  sphere(tot6/2.5);
  popMatrix();
}

void siete() {


  tot7= disenos.getInt(3, 3)+disenos.getInt(3, 6);
  resi7p= disenos.getInt(3, 1);
  resi7c= disenos.getInt(3, 4);
  nresi7p= disenos.getInt(3, 2);
  nresi7c= disenos.getInt(3, 5);

  rp7=map(resi7p, 0, 645, 0, 360);
  rc7=map(resi7c, 0, 645, 0, 360);
  nrp7=map(nresi7p, 0, 645, 0, 360);
  nrc7=map(nresi7c, 0, 645, 0, 360);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 2007
  stroke(255); //BLANCO
  arc(0, 0, tot7, tot7, radians(0), radians(rp7) );
  //arco residentes concedidos 2007
  stroke(150); //GRIS CLARO
  arc(0, 0, tot7, tot7, radians(rp7), radians(rp7+rc7) );

  //arco no residentes presentados 2007
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot7, tot7, radians(rp7+rc7), radians(rp7+rc7+nrp7) );
  //arco no residentes concedidos 2007
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot7, tot7, radians(rp7+rc7+nrp7), radians(rp7+rc7+nrp7+nrc7) );


  //esfera total 2007 

 stroke(178-12, 126-12, 192-12);
  strokeWeight(0.3);
  fill(178, 126, 192);//SIMPLY VIOLET
  sphere(tot7/2.5);
  popMatrix();
}

void ocho() {


  tot8= disenos.getInt(4, 3)+disenos.getInt(4, 6);
  resi8p= disenos.getInt(4, 1);
  resi8c= disenos.getInt(4, 4);
  nresi8p= disenos.getInt(4, 2);
  nresi8c= disenos.getInt(4, 5);

  rp8=map(resi8p, 0, 850, 0, 360);
  rc8=map(resi8c, 0, 850, 0, 360);
  nrp8=map(nresi8p, 0, 850, 0, 360);
  nrc8=map(nresi8c, 0, 850, 0, 360);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 2008
  stroke(255); //BLANCO
  arc(0, 0, tot8, tot8, radians(0), radians(rp8) );
  //arco residentes concedidos 2008
  stroke(150); //GRIS CLARO
  arc(0, 0, tot8, tot8, radians(rp8), radians(rp8+rc8) );

  //arco no residentes presentados 2008
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot8, tot8, radians(rp8+rc8), radians(rp8+rc8+nrp8) );
  //arco no residentes concedidos 2008
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot8, tot8, radians(rp8+rc8+nrp8), radians(rp8+rc8+nrp8+nrc8) );


  //esfera total 2008 

   stroke(91-12, 62-12, 85-12);
  strokeWeight(0.3);
  fill(91, 62, 85);//INEVER KNEW THIS
  sphere(tot8/2.5);
  popMatrix();
}

void nueve() {


  tot9= disenos.getInt(5, 3)+disenos.getInt(5, 6);
  resi9p= disenos.getInt(5, 1);
  resi9c= disenos.getInt(5, 4);
  nresi9p= disenos.getInt(5, 2);
  nresi9c= disenos.getInt(5, 5);

  rp9=map(resi9p, 0, 677, 0, 360);
  rc9=map(resi9c, 0, 677, 0, 360);
  nrp9=map(nresi9p, 0, 677, 0, 360);
  nrc9=map(nresi9c, 0, 677, 0, 360);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 2009
  stroke(255); //BLANCO
  arc(0, 0, tot9, tot9, radians(0), radians(rp9) );
  //arco residentes concedidos 2009
  stroke(150); //GRIS CLARO
  arc(0, 0, tot9, tot9, radians(rp9), radians(rp9+rc9) );

  //arco no residentes presentados 2009
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot9, tot9, radians(rp9+rc9), radians(rp9+rc9+nrp9) );
  //arco no residentes concedidos 2009
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot9, tot9, radians(rp9+rc9+nrp9), radians(rp9+rc9+nrp9+nrc9) );


  //esfera total 2009 

   stroke(247-12, 251-12, 248-12);
  strokeWeight(0.3);
  fill(247, 251, 248);//F7FBF8
  sphere(tot9/2.5);
  popMatrix();
}
void diez() {


  tot10= disenos.getInt(6, 3)+disenos.getInt(6, 6);
  resi10p= disenos.getInt(6, 1);
  resi10c= disenos.getInt(6, 4);
  nresi10p= disenos.getInt(6, 2);
  nresi10c= disenos.getInt(6, 5);

  rp10=map(resi10p, 0, 733, 0, 360);
  rc10=map(resi10c, 0, 733, 0, 360);
  nrp10=map(nresi10p, 0, 733, 0, 360);
  nrc10=map(nresi10c, 0, 733, 0, 360);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 2010
  stroke(255); //BLANCO
  arc(0, 0, tot10, tot10, radians(0), radians(rp10) );
  //arco residentes concedidos 2010
  stroke(150); //GRIS CLARO
  arc(0, 0, tot10, tot10, radians(rp10), radians(rp10+rc10) );

  //arco no residentes presentados 2010
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot10, tot10, radians(rp10+rc10), radians(rp10+rc10+nrp10) );
  //arco no residentes concedidos 20010
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot10, tot10, radians(rp10+rc10+nrp10), radians(rp10+rc10+nrp10+nrc10) );


  //esfera total 2010 

   stroke(166-12, 203-12, 197-12);
  strokeWeight(0.3);
  fill(166, 203, 197);//CYAN SEASCAPE
  sphere(tot10/2.5);
  popMatrix();
}

void once() {


  tot11= disenos.getInt(7, 3)+disenos.getInt(7, 6);
  resi11p= disenos.getInt(7, 1);
  resi11c= disenos.getInt(7, 4);
  nresi11p= disenos.getInt(7, 2);
  nresi11c= disenos.getInt(7, 5);

  rp11=map(resi11p, 0, 1156, 0, 370);
  rc11=map(resi11c, 0, 1156, 0, 370);
  nrp11=map(nresi11p, 0, 1156, 0, 370);
  nrc11=map(nresi11c, 0, 1156, 0, 370);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 20011
  stroke(255); //BLANCO
  arc(0, 0, tot11, tot11, radians(0), radians(rp11) );
  //arco residentes concedidos 2011
  stroke(150); //GRIS CLARO
  arc(0, 0, tot11, tot11, radians(rp11), radians(rp11+rc11) );

  //arco no residentes presentados 2011
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot11, tot11, radians(rp11+rc11), radians(rp11+rc11+nrp11) );
  //arco no residentes concedidos 2011
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot11, tot11, radians(rp11+rc11+nrp11), radians(rp11+rc11+nrp11+nrc11) );


  //esfera total 2011

 stroke(75-12, 181-12, 155-12);
  strokeWeight(0.3);
  fill(75, 181, 155);//SEA GLASS
  sphere(tot11/2.5);
  popMatrix();
}

void doce() {


  tot12= disenos.getInt(8, 3)+disenos.getInt(8, 6);
  resi12p= disenos.getInt(8, 1);
  resi12c= disenos.getInt(8, 4);
  nresi12p= disenos.getInt(8, 2);
  nresi12c= disenos.getInt(8, 5);

  rp12=map(resi12p, 0, 940, 0, 370);
  rc12=map(resi12c, 0, 940, 0, 370);
  nrp12=map(nresi12p, 0, 940, 0, 370);
  nrc12=map(nresi12c, 0, 940, 0, 370);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 2012
  stroke(255); //BLANCO
  arc(0, 0, tot12, tot12, radians(0), radians(rp12) );
  //arco residentes concedidos 20012
  stroke(150); //GRIS CLARO
  arc(0, 0, tot12, tot12, radians(rp12), radians(rp12+rc12) );

  //arco no residentes presentados 2012
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tot12, tot12, radians(rp12+rc12), radians(rp12+rc12+nrp12) );
  //arco no residentes concedidos 2012
  stroke(80); //GRIS OSCURO
  arc(0, 0, tot12, tot12, radians(rp12+rc12+nrp12), radians(rp12+rc12+nrp12+nrc12) );


  //esfera total 2012

   stroke(199-12, 76-12, 92-12);
  strokeWeight(0.3);
  fill(199, 76, 92);//WANT TO COME IN?
  sphere(tot12/2.5);
  popMatrix();
}

void trece() {


  tottrece= disenos.getInt(9, 3)+disenos.getInt(9, 6);

  resi13p= disenos.getInt(9, 1);
  resi13c= disenos.getInt(9, 4);
  nresi13p= disenos.getInt(9, 2);
  nresi13c= disenos.getInt(9, 5);

  rp13=map(resi13p, 0, 1302, 0, 370);
  rc13=map(resi13c, 0, 1302, 0, 370);
  nrp13=map(nresi13p, 0, 1302, 0, 370);
  nrc13=map(nresi13c, 0, 1302, 0, 370);

  noFill();
  strokeWeight(10);

  pushMatrix();
  translate(0, 0, -2200);


  //arco residentes presentados 2013
  stroke(255); //BLANCO
  arc(0, 0, tottrece, tottrece, radians(0), radians(rp13) );
  //arco residentes concedidos 2013
  stroke(150); //GRIS CLARO
  arc(0, 0, tottrece, tottrece, radians(rp13), radians(rp13+rc13) );

  //arco no residentes presentados 2013
  stroke(100); //GRIS OSCURITO
  arc(0, 0, tottrece, tottrece, radians(rp13+rc13), radians(rp13+rc13+nrp13) );
  //arco no residentes concedidos 2013
  stroke(80); //GRIS OSCURO
  arc(0, 0, tottrece, tottrece, radians(rp13+rc13+nrp13), radians(rp13+rc13+nrp13+nrc13) );
  

  //esfera total 2013

   stroke(140-12, 51-12, 63-12);
  strokeWeight(0.3);
  fill(140, 51, 63);//TACKED ONTO EVERY
  sphere(tottrece/2.5);
  popMatrix();
}



void mouseMoved() {
  if (mouseY>135 && mouseY<195 && mouseX>40 && mouseX<140) {
    nextDegrees = -36.0;
    needsToMove = true;
    println("needsToMove = " + needsToMove);
    println("nextDegrees = " + nextDegrees);
    println("currentDegreesOfRotation = " + currentDegreesOfRotation);
  }
  //2004
  if (mouseY>75 && mouseY<135 && mouseX>40 && mouseX<140) {
    nextDegrees = 0.0;
    needsToMove = true;
  }
  //2005
  if (mouseY>135 && mouseY<195 && mouseX>40 && mouseX<140) {
    nextDegrees = -36.0;
    needsToMove = true;
  }

  //2006
  if (mouseY>195 && mouseY<255 && mouseX>40 && mouseX<140) {
    nextDegrees = -72.0;
    needsToMove = true;
  }
  //2007
  if (mouseY>255 && mouseY<315 && mouseX>40 && mouseX<140) {
    nextDegrees = -108.0;
    needsToMove = true;
  }
  //2008
  if (mouseY>315 && mouseY<375 && mouseX>40 && mouseX<140) {
    nextDegrees = -144.0;
    needsToMove = true;
  }

  //2009
  if (mouseY>375 && mouseY<435 && mouseX>40 && mouseX<140) {
    nextDegrees = -180.0;
    needsToMove = true;
  }

  //2010
  if (mouseY>435 && mouseY<495 && mouseX>40 && mouseX<140) {
    nextDegrees = -216.0;
    needsToMove = true;
  }

  //2011
  if (mouseY>495 && mouseY<555 && mouseX>40 && mouseX<140) {
    nextDegrees = -252.0;
    needsToMove = true;
  }

  //2012
  if (mouseY>555 && mouseY<615 && mouseX>40 && mouseX<140) {
    nextDegrees = -288.0;
    needsToMove = true;
  }
  //2013
  if (mouseY>615 && mouseY<675 && mouseX>40 && mouseX<140) {
    nextDegrees = -324.0;
    needsToMove = true;
  }
}
