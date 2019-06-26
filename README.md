//Variables

//Bird
int BirdY = 100;
int BridX = 100;

//Constants
int Velocity = 1;
int Gravity = 1;
int PipeSpeed = 2;
boolean randOp = true;

//LowerPipe
int LowerPipeX = 350;
int LowerPipeY = 350;

//UpperPipe
int UpperPipeX = 350;
int UpperPipeY = -350;

//Constants
void setup(){
  size(500,500);
}

void draw(){
  //BackGround
  background(135,206,250);
  
  //Bird 
  Bird();
  
  //Gravity
  Gravity();
  
  //Pipe
  LowerPipe();
  UpperPipe();
  
  //PipeTeleport
  PipeTeleport();
  
  //PipeMover
  PipeMover();
}

void Gravity(){
  //Gavity
  BirdY = BirdY + Gravity;
}

//Functions

void Bird(){
  //Bird
  fill(255,0,0);
  stroke(124,252,0);
  ellipse(BridX, BirdY, 50, 50);
}

void PipeMover(){
 LowerPipeX = LowerPipeX - PipeSpeed;  
 UpperPipeX = UpperPipeX - PipeSpeed;
}

void LowerPipe(){
  fill(0,100,0);
  rect(LowerPipeX, LowerPipeY, 50, 500);
}

void UpperPipe(){
    fill(0,100,0);
  rect(UpperPipeX, UpperPipeY, 50, 500);
}

void PipeTeleport(){
  //RandomOp
  //Bool RandOp goes from true back to false due to if statement below stating that
  int rand = (int)random(100,400);
  
  //Moving Pipe
  if (LowerPipeX < 0){
    LowerPipeX = 450;
    if (randOp == true){
      print(randOp);
      randOp = false;
      LowerPipeY = LowerPipeY - rand;
      UpperPipeY = UpperPipeY + rand;
    }
  }
  if (UpperPipeX < 0){
   UpperPipeX = 450;
   if(randOp == false)
    print(randOp);
    LowerPipeY = LowerPipeY + rand;
    UpperPipeY = UpperPipeY - rand;
    randOp = true;
   }
  }

void mousePressed(){
  //Jump
  BirdY = BirdY - 30;
}
