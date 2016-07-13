# openGL
openGL mini project.
Based on smart homes.
Menu-driven UI.
Rough Code.
/*
 * cg_proj.c
 *
 *  Created on: 19-Apr-2016
 *      Author: Prabhjot Singh
 */

#include <stdlib.h>
#include <GLUT/glut.h>
#include<string.h>
#include<stdio.h>
#define maxx 10
#define maxy 12
#define dx 27.7
#define dy 12

int x= -150, c=0;
int x2=0, y1=0, x3=0, y3=0, x4=0, y4=0;
int x6=0, y6=0;
int flag=0,scene=-1;
int x1=-150;

void *fonts[] = { GLUT_BITMAP_9_BY_15,
    GLUT_BITMAP_TIMES_ROMAN_10,
    GLUT_BITMAP_TIMES_ROMAN_24,
    GLUT_BITMAP_HELVETICA_18,
    GLUT_BITMAP_HELVETICA_12 };

/*-------------------------------------------------------------------*/
/*****************************SCENE 1****************************/
/*-------------------------------------------------------------------*/

//void sky()
//{
//    glBegin(GL_QUADS);
//    glColor3f(0, 0.8, 0.8);
//    
//    glVertex2i(1000, 300);
//    glVertex2i(1000, 600);
//    glVertex2i(0, 600);
//    glVertex2i(0, 300);
//    glEnd();
//}
void output(int x, int y, char *string, void *font)
{
    int len, i;
    glRasterPos2f(x, y);
    len = (int)strlen(string);
    for (i = 0; i<len; i++)
    {
        glutBitmapCharacter(font, string[i]);
    }
}

void menu()
{
    glColor3f(0.545098039, 0.211764705, 0.149019607);
    output(500, 550, "Smart Homes", fonts[2]);
    
    glColor3f(0.545098039, 0.101960784, 0.101960784);
    output(450, 450, "MENU", fonts[3]);
    
    glColor3f(0.545098039, 0.298039215, 0.223529411);
    output(430, 420, "1. Gate Automation", fonts[2]);
    output(430, 380, "2. Face Recognition System", fonts[2]);
    output(430, 340, "3. Smart Rooms", fonts[2]);
    output(430, 300, "4. EXIT", fonts[2]);
    
    glColor3f(0.545098039, 0.270588235, 0.074509803);
    output(380, 200, " Press the desired option to continue", fonts[2]);
    //output(380, 80, "Press 'm' to return to menu", fonts[2]);
    
}

void car()
{
    glColor3f(0,0,0);
    
    glPushMatrix();
    glTranslatef(180-2+4,195,10);
    glutSolidTorus(5,15,100,90);
    glPopMatrix();
    
    glPushMatrix();
    glTranslatef(333+4,195,10);
    glutSolidTorus(5,15,100,90);
    glPopMatrix();
    
    glColor3f(.5,.5,.5);
    
    glPushMatrix();
    glTranslatef(333+4,195,70);
    glutSolidTorus(0,5,10,69);
    glPopMatrix();
    
    glPushMatrix();
    glTranslatef(180-2+4,195,70);
    glutSolidTorus(0,5,10,69);
    glPopMatrix();
    
    //car bottom
    glBegin(GL_QUADS);
    
       glColor3f(0,1,1);
       glVertex2f(155,195);
       glVertex2f(360,195);
       glVertex2f(360,230);
       glVertex2f(155,230);
    
    glEnd();
    
    //car top
    glBegin(GL_QUADS);
    
        glColor3f(0, 0.5, 0.5);
        glVertex2i(180, 230);
        glVertex2i(215, 270);
        glVertex2i(300, 270);
        glVertex2i(325, 230);
    glEnd();
    
    //headlight
    glBegin(GL_QUADS);
    
        glColor3f(1,0.8,0);
        glVertex2i(360, 205);
        glVertex2i(349, 205);
        glVertex2i(349, 230);
        glVertex2i(360, 230);
    
    glEnd();
    
    glBegin(GL_LINES);
    glColor3f(0, 0, 0);
    glVertex2i(260, 270);
    glVertex2i(260, 230);
    glEnd();
    
}
void wheel_front()
{
    glColor3f(0,0,0);
    
    glPushMatrix();
    glTranslatef(182-5,193,70);
    glutSolidTorus(5,15,100,90);
    glPopMatrix();
    
    glPushMatrix();
    glTranslatef(337-5,193,70);
    glutSolidTorus(5,15,100,90);
    glPopMatrix();            //back two wheels tyre
    
    glColor3ub(100,100,100);
    
    glPushMatrix();
    glTranslatef(337-5,193,70);
    glutSolidTorus(5,5,10,69);
    glPopMatrix();
    
    glPushMatrix();
    glTranslatef(182-5,193,70);
    glutSolidTorus(5,5,10,69);
    glPopMatrix();      //back two wheels

}


void road2d()
{
    /************** left part of road  *********/
    int x;
//    glColor3ub(7,255,130);
//    glBegin(GL_POLYGON);
//    glVertex2i(0,650);
//    glVertex2i(1000,650);
//    glVertex2i(1000,0);
//    glVertex2i(0,0);
//    glEnd();
//    
    glColor3ub(30,40,50);
    glBegin(GL_POLYGON);
    glVertex2i(0,420-175);
    glVertex2i(1000,420-175);
    glVertex2i(1000,300-175);
    glVertex2i(0,300-175);
    glEnd();
    
    
    
    /************  STRIPES  ************/
    
    glColor3f(1.0,0.9,0.0);
    for(x=0;x<1000;x=x+60)
    {
        glBegin(GL_POLYGON);
        glVertex2f(x,352.5+19-175);
        glVertex2f(x,357.5+19-175);
        glVertex2f(x+30,357.5+19-175);
        glVertex2f(x+30,352.5+19-175);
        glEnd();
    }
    
    glColor3f(0, 0, 0);
    output(340, 50, "Press 'm' to return to menu", fonts[2]);
    
}







/*-------------------------------------------------------------------*/
//	FUNCTION text
/*-------------------------------------------------------------------*/

void textd()
{
    
    char string1[]="Press Right Arrow key to move the car --> ";
    void *font1=GLUT_BITMAP_TIMES_ROMAN_24;
    
    int j;
    /******** JSSATE ********/
    
    
    glRasterPos3f(420-80,602-530,-120);
    for(j=0;j<strlen(string1);j++)
        glutBitmapCharacter(font1,string1[j]);

}

void text1d()
{
    char string2[]="House Bus";
    void *font2=GLUT_BITMAP_TIMES_ROMAN_24;
    int k;
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(230,400-175,70);
    for(k=0;k<strlen(string2);k++)
        glutBitmapCharacter(font2,string2[k]);
}

void text2d()
{
    char string2[]="Mannat";
    void *font2=GLUT_BITMAP_TIMES_ROMAN_24;
    int k;
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(295,400,70);
    for(k=0;k<strlen(string2);k++)
        glutBitmapCharacter(font2,string2[k]);
    
    char string3[]="Residence";
    void *font3=GLUT_BITMAP_TIMES_ROMAN_24;
    
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(270,380,70);
    for(k=0;k<strlen(string3);k++)
        glutBitmapCharacter(font3,string3[k]);
    
    char string4[]="Domlur";
    void *font4=GLUT_BITMAP_TIMES_ROMAN_24;
    
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(300,360,70);
    for(k=0;k<strlen(string4);k++)
        glutBitmapCharacter(font4,string4[k]);
    
    char string5[]="Bangalore";
    void *font5=GLUT_BITMAP_TIMES_ROMAN_24;
    
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(270,340,70);
    for(k=0;k<strlen(string5);k++)
        glutBitmapCharacter(font5,string5[k]);
    
    
}

void buildingd()
{
    //buliding
    glColor3ub(255,70,20);
    double len=300;
    double thick=390;
    glPushMatrix();
    glTranslatef(650+55,520,70.0);
    glScalef(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //door
    glColor3f(0.0,0.6,0.7);
    double len1=50;
    double thick1=80;
    glPushMatrix();
    glTranslatef(650+55,520-125,70.0);
    glScalef(thick1,len1,thick1);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3ub(0,0,0);
    glBegin(GL_LINE_LOOP);
    glVertex2i(550+115,550-130);
    glVertex2i(630+115,550-130);
    glVertex2i(630+115,520-150);
    glVertex2i(550+115,520-150);
    glEnd();
    glBegin(GL_LINES);
    glVertex2i(704,550-130);
    glVertex2i(704,520-150);
    glEnd();
    
    //windows
    
    glColor3f(0.0,0.6,0.7);
    double len2=30;
    double thick2=30;
    glPushMatrix();
    glTranslatef(650-100,520,70.0);
    glScalef(thick2,len2,thick2);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len3=30;
    double thick3=30;
    glPushMatrix();
    glTranslatef(650,520,70.0);
    glScalef(thick3,len3,thick3);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len4=30;
    double thick4=30;
    glPushMatrix();
    glTranslatef(650+100,520,70.0);
    glScalef(thick4,len4,thick4);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len5=30;
    double thick5=30;
    glPushMatrix();
    glTranslatef(650+200,520,70.0);
    glScalef(thick5,len5,thick5);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len6=30;
    double thick6=30;
    glPushMatrix();
    glTranslatef(650-100,520+100,70.0);
    glScalef(thick6,len6,thick6);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len7=30;
    double thick7=30;
    glPushMatrix();
    glTranslatef(650,520+100,70.0);
    glScalef(thick7,len7,thick7);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len8=30;
    double thick8=30;
    glPushMatrix();
    glTranslatef(650+100,520+100,70.0);
    glScalef(thick8,len8,thick8);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len9=30;
    double thick9=30;
    glPushMatrix();
    glTranslatef(650+200,520+100,70.0);
    glScalef(thick9,len9,thick9);
    glutSolidCube(1.0);
    glPopMatrix();
    
}

void walld()
{
    int i,j;
    float x0={750.0},y01={300.0};
    float x[maxx]={40.0},y[maxy]={20.0};
    float xc={0.0},yc={300.0};
    //wall left
    glColor3ub(200,50,50);
    glBegin(GL_POLYGON);
    glVertex2i(600+150,433);
    glVertex2i(900+150,433);
    glVertex2i(900+150,300);
    glVertex2i(600+150,300);
    glEnd();
    
    
    
    
    //brick left
    
    for(i=0;i<maxx;i++)
        x[i]=x0+i*dx;
    for(j=0;j<maxy;j++)
        y[j]=y01+j*dy;
    
    for(i=0;i<maxx-1;i++)
        for(j=0;j<maxy-1;j++)
        {
            glColor3f(0.0,0.0,0.0);
            glBegin(GL_LINE_LOOP);
            glVertex2f(x[i],y[j]);
            glVertex2f(x[i+1],y[j]);
            glVertex2f(x[i+1],y[j+1]);
            glVertex2f(x[i],y[j+1]);
            glEnd();
        }
    
    //wall right
    glColor3ub(200,50,50);
    glBegin(GL_POLYGON);
    glVertex2i(0-50,433);
    glVertex2i(300-50,433);
    glVertex2i(300-50,300);
    glVertex2i(0-50,300);
    glEnd();
    
    
    
    
    //brick right
    
    for(i=0;i<maxx;i++)
        x[i]=xc+i*dx;
    for(j=0;j<maxy;j++)
        y[j]=yc+j*dy;
    
    for(i=0;i<maxx-1;i++)
        for(j=0;j<maxy-1;j++)
        {
            glColor3f(0.0,0.0,0.0);
            glBegin(GL_LINE_LOOP);
            glVertex2f(x[i],y[j]);
            glVertex2f(x[i+1],y[j]);
            glVertex2f(x[i+1],y[j+1]);
            glVertex2f(x[i],y[j+1]);
            glEnd();
        }
    
    
    
    //wall middle
    
    glColor3ub(250,220,220);
    glBegin(GL_POLYGON);
    glVertex2i(250,433);
    glVertex2i(300+80,433);
    glVertex2i(300+80,300);
    glVertex2i(250,300);
    glEnd();
    
    glColor3ub(255,200,200);
    glBegin(GL_POLYGON);
    glVertex2i(260,423);
    glVertex2i(300+70,423);
    glVertex2i(300+70,310);
    glVertex2i(260,310);
    glEnd();
    
    
}

void gated()
{
    
    
    //gate right
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(750,300);
    glVertex2i(600,300);
    glVertex2i(600,303);
    glVertex2i(750,303);
    glEnd();
    
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(600,300);
    glVertex2i(600,450);
    glVertex2i(597,450);
    glVertex2i(597,303);
    glEnd();
    
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(600,450);
    glVertex2i(750,433);
    glVertex2i(750,430);
    glVertex2i(600,447);
    glEnd();
    
    //gate left
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(380,300);
    glVertex2i(600-5,300);
    
    glVertex2i(600-5,303);
    glVertex2i(380,303);
    glEnd();
    
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(380,433);
    glVertex2i(500+100-5,473-25);
    
    glVertex2i(500+100-5,476-23);
    glVertex2i(380,433+3);
    glEnd();
    
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(500-1+100-5,300+c);
    glVertex2i(500-1+100-5,473-23+c);
    
    glVertex2i(500-4+100-5,476-23);
    glVertex2i(500-4+100-5,303);
    glEnd();

    
}

void gateOpen()
{
    if(c<=70)
    {
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(380,300);
    glVertex2i(600-5-c,300+c);
    
    glVertex2i(600-5-c,303+c);
    glVertex2i(380,303);
    glEnd();
    
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(380,433);
    glVertex2i(500+100-5-c,473-25+c);
    
    glVertex2i(500+100-5-c,476-23+c);
    glVertex2i(380,433+3);
    glEnd();
    
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(500-1+100-5-c,300+c);
    glVertex2i(500-1+100-5-c,473-23+c);
    
    glVertex2i(500-4+100-5-c,476-23+c);
    glVertex2i(500-4+100-5-c,303+c);
    glEnd();
        
        //gate right
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(750,300);
        glVertex2i(600+c,300+c);
        glVertex2i(600+c,303+c);
        glVertex2i(750,303);
        glEnd();
        
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(600+c,300+c);
        glVertex2i(600+c,450+c);
        glVertex2i(597+c,450+c);
        glVertex2i(597+c,303+c);
        glEnd();
        
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(600+c,450+c);
        glVertex2i(750,433);
        glVertex2i(750,430);
        glVertex2i(600+c,447+c);
        glEnd();

    
    c+=10;
    }
    else{
        
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(380,300);
        glVertex2i(600-5-70,300+70);
        
        glVertex2i(600-5-70,303+70);
        glVertex2i(380,303);
        glEnd();
        
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(380,433);
        glVertex2i(500+100-5-70,473-25+70);
        
        glVertex2i(500+100-5-70,476-23+70);
        glVertex2i(380,433+3);
        glEnd();
        
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(500-1+100-5-70,300+70);
        glVertex2i(500-1+100-5-70,473-23+70);
        
        glVertex2i(500-4+100-5-70,476-23+70);
        glVertex2i(500-4+100-5-70,303+70);
        glEnd();
        
        //right
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(750,300);
        glVertex2i(600+70,300+70);
        glVertex2i(600+70,303+70);
        glVertex2i(750,303);
        glEnd();
        
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(600+70,300+70);
        glVertex2i(600+70,450+70);
        glVertex2i(597+70,450+70);
        glVertex2i(597+70,303+70);
        glEnd();
        
        glBegin(GL_POLYGON);
        glColor3ub(0,0,0);
        glVertex2i(600+70,450+70);
        glVertex2i(750,433);
        glVertex2i(750,430);
        glVertex2i(600+70,447+70);
        glEnd();


    }

}

void treed()
{
    
    //trunk1
    glColor3ub(95,6,5);
    double len=100;
    double thick=15;
    glPushMatrix();
    glTranslated(100+850,150+330,0.0);
    glScaled(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //leaves1
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    
    glTranslated(100+850,230+290,0.0);
    glutSolidCone(60,120,3,2);
    glPopMatrix();
    
    //leaves2
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100+850,260+290,0.0);
    glutSolidCone(50,100,3,2);
    glPopMatrix();
    
    // leaves3
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100+850,290+290,0);
    glutSolidCone(40,800,3,2);
    glPopMatrix();
}
void tree1d()
{
    //trunk1
    glColor3ub(95,6,5);
    double len=100;
    double thick=15;
    glPushMatrix();
    glTranslated(100,150+330,0.0);
    glScaled(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //leaves1
    
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    
    glTranslated(100,230+290,0.0);
    glutSolidCone(60,120,3,2);
    glPopMatrix();
    
    //leaves2
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100,260+290,0.0);
    glutSolidCone(50,100,3,2);
    glPopMatrix();
    
    // leaves3
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100,290+290,0);
    glutSolidCone(40,800,3,2);
    glPopMatrix();
}
void tree2d()
{
    //trunk1
    glColor3ub(95,6,5);
    double len=100;
    double thick=15;
    glPushMatrix();
    glTranslated(200,150+330,0.0);
    glScaled(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //leaves1
    
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    
    glTranslated(200,230+290,0.0);
    glutSolidCone(60,120,3,2);
    glPopMatrix();
    
    //leaves2
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(200,260+290,0.0);
    glutSolidCone(50,100,3,2);
    glPopMatrix();
    
    // leaves3
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(200,290+290,0);
    glutSolidCone(40,800,3,2);
    glPopMatrix();
}

void shrubd()
{
    glColor3ub(0,160,0);
    double len0=57;
    double thick0=13;
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115,107,0);
    glScalef(len0,thick0,len0);
    glutSolidCube(1.0);
    glPopMatrix();
    //leaves1
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(100,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves2
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115,145,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves3
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(130,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    
    //flower1
    
    glColor3ub(140,0,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(130,120,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
    
    
    //flower2
    glColor3ub(140,0,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(112,143,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
}
void shrub1d()
{
    glColor3ub(0,160,0);
    double len0=57;
    double thick0=13;
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115+200,107,0);
    glScalef(len0,thick0,len0);
    glutSolidCube(1.0);
    glPopMatrix();
    //leaves1
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(100+200,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves2
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115+200,145,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves3
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(130+200,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    
    //flower1
    
    glColor3ub(200,200,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(130+200,120,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
    
    
    //flower2
    glColor3ub(200,200,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(102+200,133,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
}
void shrub2d()
{
    glColor3ub(0,160,0);
    double len0=57;
    double thick0=13;
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115+400,107,0);
    glScalef(len0,thick0,len0);
    glutSolidCube(1.0);
    glPopMatrix();
    //leaves1
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(100+400,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves2
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115+400,145,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves3
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(130+400,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    
    //flower1
    
    glColor3ub(200,0,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(120+400,118,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
    
    
    //flower2
    glColor3ub(200,0,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(125+400,145,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
}
void shrub3d()
{
    glColor3ub(0,160,0);
    double len0=57;
    double thick0=13;
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115+600,107,0);
    glScalef(len0,thick0,len0);
    glutSolidCube(1.0);
    glPopMatrix();
    //leaves1
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(100+600,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves2
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115+600,145,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves3
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(130+600,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    
    //flower1
    
    glColor3ub(140,0,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(105+600,125,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
    
    
    //flower2
    glColor3ub(140,0,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(102+600,143,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
}
void shrub4d()
{
    glColor3ub(0,160,0);
    double len0=57;
    double thick0=13;
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115+800,107,0);
    glScalef(len0,thick0,len0);
    glutSolidCube(1.0);
    glPopMatrix();
    //leaves1
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(100+800,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves2
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(115+800,145,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    //leaves3
    glColor3ub(0,160,0);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(130+800,120,70);
    glutSolidSphere(20,20,20);
    glPopMatrix();
    
    //flower1
    
    glColor3ub(140,50,50);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(105+800,125,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
    
    
    //flower2
    glColor3ub(140,50,50);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(102+800,143,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
    //flower3
    glColor3ub(140,50,50);
    glPushMatrix();
    glLoadIdentity();
    glTranslatef(132+800,133,70);
    glutSolidSphere(5,20,20);
    glPopMatrix();
    
}



/*-------------------------------------------------------------------*/
/*****************************SCENE 2****************************/
/*-------------------------------------------------------------------*/



void building2()
{
    
    //buliding
    glColor3ub(255,70,20);
    double len=600;
    double thick=800;
    glPushMatrix();
    glTranslatef(650+55,520-50,0.0);
    glScalef(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    
    //windows
    glColor3f(0.0,0.6,0.7);
    double len2=100;
    double thick2=100;
    glPushMatrix();
    glTranslatef(650-250,520,70.0);
    glScalef(thick2,len2,thick2);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len3=100;
    double thick3=100;
    glPushMatrix();
    glTranslatef(670,520,70.0);
    glScalef(thick3,len3,thick3);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len5=100;
    double thick5=100;
    glPushMatrix();
    glTranslatef(650+260,520,70.0);
    glScalef(thick5,len5,thick5);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len6=100;
    double thick6=100;
    glPushMatrix();
    glTranslatef(650-250,520+150,70.0);
    glScalef(thick6,len6,thick6);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len7=100;
    double thick7=100;
    glPushMatrix();
    glTranslatef(670,520+150,70.0);
    glScalef(thick7,len7,thick7);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0.0,0.6,0.7);
    double len9=100;
    double thick9=100;
    glPushMatrix();
    glTranslatef(650+260,520+150,70.0);
    glScalef(thick9,len9,thick9);
    glutSolidCube(1.0);
    glPopMatrix();
    
    output(380, 80, "Press 'm' to return to menu", fonts[2]);
    
}

void treeS2_1()
{
    //trunk1
    glColor3ub(95,6,5);
    double len=80;
    double thick=15;
    glPushMatrix();
    glTranslated(100,150+330,0.0);
    glScaled(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //leaves1
    
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    
    glTranslated(100,230+290,0.0);
    glutSolidCone(60,120,3,2);
    glPopMatrix();
    
    //leaves2
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100,260+290,0.0);
    glutSolidCone(50,100,3,2);
    glPopMatrix();
    
    // leaves3
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100,290+290,0);
    glutSolidCone(40,800,3,2);
    glPopMatrix();
}

void treeS2_2()
{
    //trunk1
    glColor3ub(95,6,5);
    double len=80;
    double thick=15;
    glPushMatrix();
    glTranslated(100+80,150+100,0.0);
    glScaled(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //leaves1
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100+80,230+60,0.0);
    glutSolidCone(80,140,3,2);
    glPopMatrix();
    
    //leaves2
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100+80,260+60,0.0);
    glutSolidCone(70,120,3,2);
    glPopMatrix();
    
    // leaves3
    
    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100+80,290+60,0);
    glutSolidCone(60,820,3,2);
    glPopMatrix();
}

void treeS2_3()
{
    //trunk1
    glColor3ub(95,6,5);
    double len=80;
    double thick=10;
    glPushMatrix();
    glTranslated(100+200,150+300,0.0);
    glScaled(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();

    //leaves1

    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100+200,230+300,0.0);
    glutSolidCone(80,140,3,2);
    glPopMatrix();

    //leaves2

    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100+200,260+300,0.0);
    glutSolidCone(70,120,3,2);
    glPopMatrix();

    // leaves3

    glColor3f(0.0,0.2,0.0);
    glPushMatrix();
    glLoadIdentity();
    glTranslated(100+200,290+300,0.0);
    glutSolidCone(60,820,3,2);
    glPopMatrix();
}

void man(int xman)
{
    
    if(x1<150)x1+=10;
    glColor3f(0,0,0);
    glPushMatrix();
    glTranslatef(540+20+xman,495-200,0);
    glutSolidTorus(1,10,100,90);
    glPopMatrix();
    glColor3ub(0,0,0);
    glPushMatrix();
    glTranslatef(540+20+xman,495-200,0);
    glutSolidTorus(7,7,100,90);
    glPopMatrix();
    
    //ear right
    glBegin(GL_POLYGON);
    glColor3ub(255,191,128);
    glVertex2i(540-14+20+xman,494+1-200);
    glVertex2i(540-14+20+xman,490+1-200);
    glVertex2i(538-14+20+xman,489+1-200);
    glVertex2i(538-14+20+xman,495+1-200);
    glEnd();
    
    //ear left
    glBegin(GL_POLYGON);
    glColor3ub(255,191,128);
    glVertex2i(554+20+xman,495-200);
    glVertex2i(556+20+xman,496-200);
    glVertex2i(556+20+xman,491-200);
    glVertex2i(554+20+xman,490-200);
    glEnd();
    
    //hair
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(527+20+xman,503-200);
    glVertex2i(553+20+xman,503-200);
    glVertex2i(547+20+xman,509-200);
    glVertex2i(533+20+xman,509-200);
    glEnd();
    
    //shirt
    glBegin(GL_POLYGON);
    glColor3ub(55,50,70);
    glVertex2i(529+20+xman,480-200);
    glVertex2i(551+20+xman,480-200);
    glVertex2i(566+20+xman,469-200);
    glVertex2i(561+20+xman,461-200);
    glVertex2i(556+20+xman,465-250);
    glVertex2i(556+20+xman,445-250);
    glVertex2i(524+20+xman,445-250);
    glVertex2i(524+20+xman,465-250);
    glVertex2i(519+20+xman,460-200);
    glVertex2i(514+20+xman,469-200);
    glEnd();
    
    //hands
    glBegin(GL_POLYGON);
    glColor3ub(255,191,128);
    glVertex2i(565+20+xman,468-200);
    glVertex2i(575+20+xman,453-200);
    glVertex2i(567+20+xman,454-200);
    glVertex2i(562+20+xman,462-200);
    glEnd();
    glBegin(GL_POLYGON);
    glVertex2i(575+20+xman,453-200);
    glVertex2i(556+20+xman,438-200);
    glVertex2i(556+20+xman,445-200);
    glVertex2i(567+20+xman,454-200);
    glEnd();
    glBegin(GL_POLYGON);
    glVertex2i(515+20+xman,468-200);
    glVertex2i(505+20+xman,453-200);
    glVertex2i(513+20+xman,454-200);
    glVertex2i(518+20+xman,462-200);
    glEnd();
    glBegin(GL_POLYGON);
    glVertex2i(505+20+xman,453-200);
    glVertex2i(524+20+xman,438-200);
    glVertex2i(524+20+xman,445-200);
    glVertex2i(513+20+xman,454-200);
    glEnd();
    
    //pant
    glBegin(GL_POLYGON);
    glColor3ub(80,80,230);
    glVertex2i(555+20+xman,440-230);
    glVertex2i(525+20+xman,440-230);
    glVertex2i(520+20+xman,405-250);
    glVertex2i(530+20+xman,405-250);
    glVertex2i(533+20+xman,438-250);
    glVertex2i(550+40+xman,405-250);
    glVertex2i(560+40+xman,405-250);
    glEnd();
    
    //shoe left
    glBegin(GL_POLYGON);
    glColor3ub(100,10,10);
    glVertex2i(530+20+xman,405-250);
    glVertex2i(530+20+xman,396-250);
    glVertex2i(512+20+xman,396-250);
    glVertex2i(520+20+xman,405-250);
    glEnd();
    
    //shoe right
    glBegin(GL_POLYGON);
    glColor3ub(100,40,10);
    glVertex2i(550+40+xman,405-250);
    glVertex2i(550+40+xman,396-250);
    glVertex2i(568+40+xman,396-250);
    glVertex2i(560+40+xman,405-250);
    glEnd();
    
  //  glutPostRedisplay();
    
    output(400, 50, "Press 'Up' arrow key to move the man", fonts[2]);
    
}

void faceRec()
{
    //facerecognize
    
    x2=247;
    y1=245;
    
    //box
    double len8=55;
    double thick8=50;
    glColor3f(0.9,0.9,0.9);
    glPushMatrix();
    glTranslatef(650+25-110,520-180-20,0.0);
    glScalef(thick8,len8,thick8);
    glutSolidCube(1.0);
    glPopMatrix();
    
    if((x1>15))
    {
    
    //face
    glColor3ub(0,0,0);
    glPushMatrix();
    glTranslatef(540-220+x2,495+76-y1,0);
    glutSolidTorus(1,10,100,90);
    glPopMatrix();
    
    glColor3ub(255,191,128);
    glPushMatrix();
    glTranslatef(540-220+x2,495+76-y1,0);
    glutSolidTorus(7,7,100,90);
    glPopMatrix();
    glColor3ub(0,0,0);
    
    glBegin(GL_LINES);
    glVertex2i(540-220+x2,495+76-y1);
    glVertex2i(540-220+x2,490+76-y1); //nose
  		glVertex2i(531-220+x2,500+76-y1);
    glVertex2i(537-220+x2,500+76-y1);//eyebrow
  		glVertex2i(543-220+x2,500+76-y1);
    glVertex2i(549-220+x2,500+76-y1);//eyebrow
    glEnd();
    //ear right
    glBegin(GL_POLYGON);
    glColor3ub(255,191,128);
    glVertex2i(540-14-220+x2,494+1+76-y1);
    glVertex2i(540-14-220+x2,490+1+76-y1);
    glVertex2i(538-14-220+x2,489+1+76-y1);
    glVertex2i(538-14-220+x2,495+1+76-y1);
    glEnd();
    //ear left
    glBegin(GL_POLYGON);
    glColor3ub(255,191,128);
    glVertex2i(554-220+x2,495+76-y1);
    glVertex2i(556-220+x2,496+76-y1);
    glVertex2i(556-220+x2,491+76-y1);
    glVertex2i(554-220+x2,490+76-y1);
    glEnd();
    //hair
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(527-220+x2,503+76-y1);
    glVertex2i(553-220+x2,503+76-y1);
    glVertex2i(547-220+x2,509+76-y1);
    glVertex2i(533-220+x2,509+76-y1);
    glEnd();
    
    
    // eyes
    glBegin(GL_POLYGON);
    glVertex2i(533-220+x2,498+76-y1);
    glVertex2i(535-220+x2,498+76-y1);
    glVertex2i(535-220+x2,496+76-y1);
    glVertex2i(533-220+x2,496+76-y1);
    glEnd();
    glBegin(GL_POLYGON);
    glVertex2i(545-220+x2,498+76-y1);
    glVertex2i(547-220+x2,498+76-y1);
    glVertex2i(547-220+x2,496+76-y1);
    glVertex2i(545-220+x2,496+76-y1);
    glEnd();
    // mouth
    glBegin(GL_POLYGON);
    glVertex2i(535-220+x2,487+76-y1);
    glVertex2i(540-220+x2,485+76-y1);
    glVertex2i(545-220+x2,487+76-y1);
    glVertex2i(540-220+x2,487+76-y1);
    glEnd();
    //beard
    glBegin(GL_POLYGON);
    glColor3ub(0,0,0);
    glVertex2i(538-220+x2,480+76-y1);
    glVertex2i(542-220+x2,480+76-y1);
    glVertex2i(542-220+x2,484+76-y1);
    glVertex2i(538-220+x2,484+76-y1);
    glEnd();
    }
    
    
    }

void faceButton()
{
    glPushMatrix();
    if (x1>30)
    {
        glColor3f(0, 1, 0);
    }
    else
        glColor3f(0.2,0.2,0.2);
    
    double len1=25;
    double thick1=8;
    glPushMatrix();
    glTranslatef(650+80+55,520-260+25,0.0);
    glRotated(90, 1, 0, 0);
    glScalef(thick1,len1,thick1);
    glutSolidSphere(2.0,10.0, 10.0);
    glPopMatrix();
    
}

//void faceRec2()
//{
//    double len11=60;
//    double thick11=70;
//    glColor3f(0.5,1,0);
//    glPushMatrix();
//    glTranslatef(650+25,520-200,0.0);
//    glScalef(thick11,len11,thick11);
//    glutSolidCube(1.0);
//    glPopMatrix();
//    
//}

void doorInitial()
{
    //door
    glColor3f(0.5,0.1,0);
    double len12=200;
    double thick12=150;
    glPushMatrix();
    glTranslatef(650+25,520-250,70);
    glScalef(thick12,len12,thick12);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //doorhandle
    glColor3f(0,0,0);
    double len1=25;
    double thick1=8;
    glPushMatrix();
    glTranslatef(650+80,520-260,0.0);
    glScalef(thick1,len1,thick1);
    glutSolidSphere(0.5,100.0, 9.0);
    glPopMatrix();
    
    if (x1==150)            //door open
    {
        glPushMatrix();
        glBegin(GL_POLYGON);
        glColor3f(0.5,0,0);
        glVertex2i(550+50,550-380);
        glVertex2i(630+120,550-360);
        glVertex2i(630+120,520-130);
        glVertex2i(550+50,520-150);
        glEnd();
        
        //doorhandle
        glColor3f(0,0,0);
        double len1=25;
        double thick1=8;
        glPushMatrix();
        glTranslatef(650+80,520-260,0.0);
        glScalef(thick1,len1,thick1);
        // glRotated(60, 0, 1, 0);
        glutSolidSphere(0.5,100.0, 9.0);
        glPopMatrix();
        
        //behind_door
        glBegin(GL_POLYGON);
        glColor3f(0,0,0);
        glVertex2i(550+50,550-380);
        glVertex2i(630+140,550-380);
        glVertex2i(630+120,550-360);
        glEnd();
        
        glBegin(GL_POLYGON);
        glColor3f(1, 1, 0);
        glVertex2i(630+137,550-380);
        glVertex2i(630+135,520-145);
        glVertex2i(630+120,520-130);
        glVertex2i(630+120,550-360);
        glEnd();
        
    }
    
}




/*-------------------------------------------------------------------*/
/*****************************SCENE 3****************************/
/*-------------------------------------------------------------------*/
 
void sofa()
{
    //head
    x4=50;
    y4=190;
    glColor3f(0,0,0);
    glPushMatrix();
    glTranslatef(540+20-x4,495-200-y4,0);
    glutSolidTorus(15,15,100,90);
    glPopMatrix();
    glColor3ub(0,0,0);
    
//    //ear right
//    x6=7;
//    y6=185;
//    glBegin(GL_POLYGON);
//    glColor3ub(255,191,128);
//    glVertex2i(540-14+10-x6,494+1-200-10-y6);
//    glVertex2i(540-14+10-x6,490+1-200+10-y6);
//    glVertex2i(538-14+10-x6,489+1-200-10-y6);
//    glVertex2i(538-14+10-x6,495+1-200+10-y6);
//    glEnd();
//    
//    //ear left
//    glBegin(GL_POLYGON);
//    glColor3ub(255,191,128);
//    glVertex2i(554+20,495-200);
//    glVertex2i(556+20,496-200);
//    glVertex2i(556+20,491-200);
//    glVertex2i(554+20,490-200);
//    glEnd();
    
    //remote
    x6=-10;
    y6=190;
    glBegin(GL_POLYGON);
    glColor3f(0.4,0.4,0.4);
    glVertex2i(527+35-x6,503-200+10-y6);
    glVertex2i(553+35-x6,503-200+10-y6);
    glVertex2i(547+35-x6,509-200+20-y6);
    glVertex2i(533+35-x6,509-200+20-y6);
    glEnd();
    
    //remote buttons
    glColor3f(0,0,0);
    double len1=1;
    double thick1=1;
    glPushMatrix();
    glTranslatef(650+80,520-260,0.0);
    glScalef(thick1,len1,thick1);
    glutSolidSphere(0.5,100.0, 9.0);
    glPopMatrix();
    //sofa
    
    glColor3f(0.2,0,0);
    double len=200;
    double thick=400;
    glPushMatrix();
    glTranslatef(650-150,00,70.0);
    glScalef(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();



}

void walls()
{
    x3=100;
    y3=100;
    //upper ceiling
    glBegin(GL_QUADS);
    if(flag==1)
        glColor3f(0.5, 0.5, 0.5);
    glColor3f(1, 1, 0.4);
    glVertex2i(0, 650);
    glVertex2i(100+x3, 550-y3);
    glVertex2i(900-x3, 550-y3);
    glVertex2i(1000, 650);
    glEnd();
    
    //border ceiling wall
    glBegin(GL_LINES);
    glLineWidth(2.5);
    glColor3f(0,0,0);
    glVertex2i(0, 650);
    glVertex2i(100+x3, 550-y3);
    
    glVertex2i(100+x3, 550-y3);
    glVertex2i(900-x3, 550-y3);
    
    glVertex2i(900-x3, 550-y3);
    glVertex2i(1000, 650);
    glEnd();
    
    //left wall
    glBegin(GL_QUADS);
    if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
        
    glColor3f(0.5, 1, 1);
    glVertex2i(0, 650);
    glVertex2i(100+x3, 550-y3);
    glVertex2i(100+x3, 100+y3);
    glVertex2i(0, 0);
    glEnd();
    
    //border left wall
    glBegin(GL_LINES);
    glLineWidth(2.5);
    glColor3f(0,0,0);
    glVertex2i(0, 650);
    glVertex2i(100+x3, 550-y3);
    
    glVertex2i(100+x3, 550-y3);
    glVertex2i(100+x3, 100+y3);
    
    glVertex2i(100+x3, 100+y3);
    glVertex2i(0, 0);
    
    glVertex2i(100+x3, 100+y3);
    glVertex2i(900+x3, 100+y3);
    glEnd();
    
    //right wall
    glBegin(GL_QUADS);
    if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    glColor3f(0.5, 1, 1);
    glVertex2i(1000, 650);
    glVertex2i(900-x3, 550-y3);
    glVertex2i(900-x3, 100+y3);
    glVertex2i(1000, 0);
    glEnd();
    
    //border right wall
    glBegin(GL_LINES);
    glLineWidth(2.5);
    glColor3f(0,0,0);
    glVertex2i(1000, 650);
    glVertex2i(900-x3, 550-y3);
    
    glVertex2i(900-x3, 550-y3);
    glVertex2i(900-x3, 100+y3);
    
    glVertex2i(900-x3, 100+y3);
    glVertex2i(1000, 0);
    glEnd();
    
    //floor
    glBegin(GL_QUADS);
    if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    glColor3f(1, 1, 1);
    glVertex2i(0, 0);
    glVertex2i(100+x3, 100+y3);
    glVertex2i(900-x3, 100+y3);
    glVertex2i(1000, 0);
    glEnd();
    
    //floor border
    glBegin(GL_LINES);
    glColor3f(0,0,0);
    
    glVertex2i(0, 0);
    glVertex2i(100+x3, 100+y3);
    
    glVertex2i(100+x3, 100+y3);
    glVertex2i(900-x3, 100+y3);
    
    glVertex2i(900-x3, 100+y3);
    glVertex2i(1000, 0);
    glEnd();
    
    output(180, 550, "Press 'm' to return to menu", fonts[2]);

    
}

void walls2()
{
    x3=100;
    y3=100;
    
    //front wall
    
    glBegin(GL_QUADS);
    glColor3f(0.5, 0.5, 0.5);
    glVertex2i(100+x3, 550-y3);
    glVertex2i(900-x3, 550-y3);
    glVertex2i(900-x3, 100+y3);
    glVertex2i(100+x3, 100+y3);
    glEnd();
    
    
    //upper ceiling
    glBegin(GL_QUADS);
    glColor3f(0.5, 0.5, 0.5);
    glVertex2i(0, 650);
    glVertex2i(100+x3, 550-y3);
    glVertex2i(900-x3, 550-y3);
    glVertex2i(1000, 650);
    glEnd();
    
    //border ceiling wall
    glBegin(GL_LINES);
    glLineWidth(2.5);
    glColor3f(0,0,0);
    glVertex2i(0, 650);
    glVertex2i(100+x3, 550-y3);
    
    glVertex2i(100+x3, 550-y3);
    glVertex2i(900-x3, 550-y3);
    
    glVertex2i(900-x3, 550-y3);
    glVertex2i(1000, 650);
    glEnd();
    
    //left wall
    glBegin(GL_QUADS);
    //if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    
    //glColor3f(0.5, 1, 1);
    glVertex2i(0, 650);
    glVertex2i(100+x3, 550-y3);
    glVertex2i(100+x3, 100+y3);
    glVertex2i(0, 0);
    glEnd();
    
    //border left wall
    glBegin(GL_LINES);
    glLineWidth(2.5);
    glColor3f(0,0,0);
    glVertex2i(0, 650);
    glVertex2i(100+x3, 550-y3);
    
    glVertex2i(100+x3, 550-y3);
    glVertex2i(100+x3, 100+y3);
    
    glVertex2i(100+x3, 100+y3);
    glVertex2i(0, 0);
    
    glVertex2i(100+x3, 100+y3);
    glVertex2i(900+x3, 100+y3);
    glEnd();
    
    //right wall
    glBegin(GL_QUADS);
    //if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
   // glColor3f(0.5, 1, 1);
    glVertex2i(1000, 650);
    glVertex2i(900-x3, 550-y3);
    glVertex2i(900-x3, 100+y3);
    glVertex2i(1000, 0);
    glEnd();
    
    //border right wall
    glBegin(GL_LINES);
    glLineWidth(2.5);
    glColor3f(0,0,0);
    glVertex2i(1000, 650);
    glVertex2i(900-x3, 550-y3);
    
    glVertex2i(900-x3, 550-y3);
    glVertex2i(900-x3, 100+y3);
    
    glVertex2i(900-x3, 100+y3);
    glVertex2i(1000, 0);
    glEnd();
    
    //floor
    glBegin(GL_QUADS);
    //if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    //glColor3f(1, 1, 1);
    glVertex2i(0, 0);
    glVertex2i(100+x3, 100+y3);
    glVertex2i(900-x3, 100+y3);
    glVertex2i(1000, 0);
    glEnd();
    
    //floor border
    glBegin(GL_LINES);
    glColor3f(0,0,0);
    
    glVertex2i(0, 0);
    glVertex2i(100+x3, 100+y3);
    
    glVertex2i(100+x3, 100+y3);
    glVertex2i(900-x3, 100+y3);
    
    glVertex2i(900-x3, 100+y3);
    glVertex2i(1000, 0);
    glEnd();
    
    output(180, 550, "Press 'm' to return to menu", fonts[2]);
    
    
}

void tv()
{
    glColor3f(0,0,0);
    double len1=70;
    double thick1=110;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+130,0.0);
    glScalef(thick1,len1,thick1);
    glutSolidCube(1.0);
    glPopMatrix();

    glColor3f(0.5,0.5,0.5);
    double len=60;
    double thick=100;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+130,0.0);
    glScalef(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //stand tv
    glColor3f(0,0,0);
    double len3=15;
    double thick3=5;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+90,0.0);
    glScalef(thick3,len3,thick3);
    glutSolidCube(1.0);
    glPopMatrix();

    glColor3f(0,0,0);
    double len4=5;
    double thick4=20;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+85,0.0);
    glScalef(thick4,len4,thick4);
    glutSolidCube(1.0);
    glPopMatrix();

    
    //table
    glColor3f(0.5,0.5,0.5);
    double len2=10;
    double thick2=300;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+80,0.0);
    glScalef(thick2,len2,thick2);
    glutSolidCube(1.0);
    glPopMatrix();


}

void tv2()
{
    glColor3f(0,0,0);
    double len1=70;
    double thick1=110;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+130,0.0);
    glScalef(thick1,len1,thick1);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(1,0,1);
    double len=60;
    double thick=100;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+130,0.0);
    glScalef(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //stand tv
    glColor3f(0,0,0);
    double len3=15;
    double thick3=5;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+90,0.0);
    glScalef(thick3,len3,thick3);
    glutSolidCube(1.0);
    glPopMatrix();
    
    glColor3f(0,0,0);
    double len4=5;
    double thick4=20;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+85,0.0);
    glScalef(thick4,len4,thick4);
    glutSolidCube(1.0);
    glPopMatrix();
    
    
    //table
    glColor3f(0.8,0,0);
    double len2=10;
    double thick2=300;
    glPushMatrix();
    glTranslatef(650+135-270,520-350+80,0.0);
    glScalef(thick2,len2,thick2);
    glutSolidCube(1.0);
    glPopMatrix();
    
}

void clockOff()
{
    GLint r = 500, p = 100;
    
    //if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
   // glColor3f(0.98, 0.91, 0.71);
    glBegin(GL_POLYGON);
    glVertex2f(200 + r, 200 + p);
    glVertex2f(200 + r, 290 + p);
    glVertex2f(250 + r, 290 + p);
    glVertex2f(250 + r, 200 + p);
    glEnd();
    
  //  if(flag==2)
       // glColor3f(0.5, 0.5, 0.5);
    glColor3f(0.0,0.0,0.0);
   // glColor3f(0.98, 0.91, 0.71);
    glBegin(GL_TRIANGLES);
    glVertex2f(185 + r, 290 + p);
    glVertex2f(265 + r, 290 + p);
    glVertex2f(225 + r, 330 + p);
    glEnd();
    
    //if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    //glColor3f(0.49, 0.04, 0.01);
    glLineWidth(4.0);
    glBegin(GL_LINE_LOOP);
    glVertex2f(200 + r, 200 + p);
    glVertex2f(200 + r, 290 + p);
    glVertex2f(185 + r, 290 + p);
    glVertex2f(225 + r, 330 + p);
    glVertex2f(265 + r, 290 + p);
    glVertex2f(250 + r, 290 + p);
    glVertex2f(250 + r, 200 + p);
    glEnd();
    
    //if(flag==2)
        glColor3f(0, 0, 0);
    
   // glColor3f(0.49, 0.04, 0.01);
    glLineWidth(2.0);
    glBegin(GL_LINE_LOOP);
    glVertex2f(205 + r, 205 + p);
    glVertex2f(205 + r, 285 + p);
    glVertex2f(245 + r, 285 + p);
    glVertex2f(245 + r, 205 + p);
    glEnd();
    
    //if(flag==2)
        glColor3f(0, 0, 0);
    
  //  glColor3f(0.0, 0.0, 0.0);
    glPointSize(7.0);
    glBegin(GL_POINTS);
    glVertex2f(225 + r, 207 + p);
    glVertex2f(207 + r, 245 + p);
    glVertex2f(225 + r, 283 + p);
    glVertex2f(243 + r, 245 + p);
    glVertex2f(225 + r, 245 + p);
    glEnd();
    
    glLineWidth(2.0);
    glBegin(GL_LINES);
    glVertex2f(225 + r, 245 + p);
    glVertex2f(225 + r, 265 + p);
    glVertex2f(225 + r, 245 + p);
    glVertex2f(240 + r, 220 + p);
    glEnd();
 
}

void clock()
{
    GLint r = 500, p = 100;
    
    if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    glColor3f(0.98, 0.91, 0.71);
    glBegin(GL_POLYGON);
    glVertex2f(200 + r, 200 + p);
    glVertex2f(200 + r, 290 + p);
    glVertex2f(250 + r, 290 + p);
    glVertex2f(250 + r, 200 + p);
    glEnd();
    
    if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    //glColor3f(0.0,0.0,1.0);
    glColor3f(0.98, 0.91, 0.71);
    glBegin(GL_TRIANGLES);
    glVertex2f(185 + r, 290 + p);
    glVertex2f(265 + r, 290 + p);
    glVertex2f(225 + r, 330 + p);
    glEnd();
    
    if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    glColor3f(0.49, 0.04, 0.01);
    glLineWidth(4.0);
    glBegin(GL_LINE_LOOP);
    glVertex2f(200 + r, 200 + p);
    glVertex2f(200 + r, 290 + p);
    glVertex2f(185 + r, 290 + p);
    glVertex2f(225 + r, 330 + p);
    glVertex2f(265 + r, 290 + p);
    glVertex2f(250 + r, 290 + p);
    glVertex2f(250 + r, 200 + p);
    glEnd();
    
    if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    
    glColor3f(0.49, 0.04, 0.01);
    glLineWidth(2.0);
    glBegin(GL_LINE_LOOP);
    glVertex2f(205 + r, 205 + p);
    glVertex2f(205 + r, 285 + p);
    glVertex2f(245 + r, 285 + p);
    glVertex2f(245 + r, 205 + p);
    glEnd();
    
    if(flag==2)
        glColor3f(0.5, 0.5, 0.5);
    
    glColor3f(0.0, 0.0, 0.0);
    glPointSize(7.0);
    glBegin(GL_POINTS);
    glVertex2f(225 + r, 207 + p);
    glVertex2f(207 + r, 245 + p);
    glVertex2f(225 + r, 283 + p);
    glVertex2f(243 + r, 245 + p);
    glVertex2f(225 + r, 245 + p);
    glEnd();
    
    glLineWidth(2.0);
    glBegin(GL_LINES);
    glVertex2f(225 + r, 245 + p);
    glVertex2f(225 + r, 265 + p);
    glVertex2f(225 + r, 245 + p);
    glVertex2f(240 + r, 220 + p);
    glEnd();
}

void dine_light()
{
    glColor3f(0.0, 0.2, 0.0);
    glBegin(GL_TRIANGLES);
    
    glVertex2f(580-60, 600-50);
    glVertex2f(600-60, 630-50);
    glVertex2f(620-60, 600-50);
    glEnd();
    
    glBegin(GL_LINES);
    glVertex2f(600-60, 580-50);
    glVertex2f(600-60, 650-50);
    glEnd();
    
    glColor3ub(255,70,20);
    double len1=25;
    double thick1=10;
    glPushMatrix();
    glTranslatef(540,500,10.0);
    glRotated(90, 1, 0, 0);
    glScalef(thick1,len1,thick1);
    glutSolidSphere(4.0,100.0, 10.0);
    glPopMatrix();
    
}

void dine_light2()
{
    //if(flag==2)
        glColor3f(0, 0, 0);
   // glColor3f(1.0, 0.0, 1.0);
    glBegin(GL_TRIANGLES);
    
    glVertex2f(580-60, 600-50);
    glVertex2f(600-60, 630-50);
    glVertex2f(620-60, 600-50);
    glEnd();
    
    glBegin(GL_LINES);
    glVertex2f(600-60, 580-50);
    glVertex2f(600-60, 650-50);
    glEnd();
    
   // if(flag==2)
        glColor3f(0, 0, 0);
   // glColor3f(0, 0, 0);
    double len1=25;
    double thick1=10;
    glPushMatrix();
    glTranslatef(540,500,10.0);
    glRotated(90, 1, 0, 0);
    glScalef(thick1,len1,thick1);
    glutSolidSphere(4.0,100.0, 10.0);
    glPopMatrix();

}

void remoteZoom()
{
    
    glColor3f(0.5,0.5,0.5);
    double len=200;
    double thick=150;
    glPushMatrix();
    glTranslatef(650+135,520-350,0.0);
    glScalef(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //button ON
    
    glColor3f(1,1,1);
    double len17=80;
    double thick17=120;
    glPushMatrix();
    glTranslatef(650+135,520-400,0.0);
    glScalef(thick17,len17,thick17);
    glutSolidCube(1.0);
    glPopMatrix();
    
    char string[]="ON";
    void *font=GLUT_BITMAP_TIMES_ROMAN_24;
    int k;
    glColor3f(0,0,0);
    glRasterPos3f(650+135,520-400,0.0);
    for(k=0;k<strlen(string);k++)
        glutBitmapCharacter(font,string[k]);
    
    //button OFF
    glColor3f(1,0,0);
    glPushMatrix();
    glTranslatef(650+135,520-300,0.0);
    glScalef(thick17,len17,thick17);
    glutSolidCube(1.0);
    glPopMatrix();
    
    
    char string1[]="OFF";
    void *font1=GLUT_BITMAP_TIMES_ROMAN_24;
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(650+135,520-290,0.0);
    for(k=0;k<strlen(string1);k++)
        glutBitmapCharacter(font1,string1[k]);
    
    output(200, 500 , "Press 'o' to switch On the lights", fonts[2]);


    

    
}

void remote2()
{
    glColor3f(0.5,0.5,0.5);
    double len=200;
    double thick=150;
    glPushMatrix();
    glTranslatef(650+135,520-350,0.0);
    glScalef(thick,len,thick);
    glutSolidCube(1.0);
    glPopMatrix();
    
    //button ON
    
    glColor3f(0,1,0);
    double len17=80;
    double thick17=120;
    glPushMatrix();
    glTranslatef(650+135,520-400,0.0);
    glScalef(thick17,len17,thick17);
    glutSolidCube(1.0);
    glPopMatrix();
    
    char string[]="ON";
    void *font=GLUT_BITMAP_TIMES_ROMAN_24;
    int k;
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(650+135,520-400,0.0);
    for(k=0;k<strlen(string);k++)
        glutBitmapCharacter(font,string[k]);
    
    //button OFF
    glColor3f(0.5,0.5,0.5);
    glPushMatrix();
    glTranslatef(650+135,520-300,0.0);
    glScalef(thick17,len17,thick17);
    glutSolidCube(1.0);
    glPopMatrix();
    
    
    char string1[]="OFF";
    void *font1=GLUT_BITMAP_TIMES_ROMAN_24;
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(650+135,520-290,0.0);
    for(k=0;k<strlen(string1);k++)
        glutBitmapCharacter(font1,string1[k]);
    
    output(200, 500 , "Press 'f' to switch Off the lights", fonts[2]);
    

}

/*-------------------------------------------------------------------*/
/*****************************INTRODUCTION****************************/
/*-------------------------------------------------------------------*/

void intro()
{
    glColor3ub(147,105,203);
    glBegin(GL_POLYGON);
    glVertex2i(0,650);
	  	glVertex2i(600,650);
    glVertex2i(800,250);
    glVertex2i(0,250);
    glEnd();
    
    glColor3ub(247,185,183);
    glBegin(GL_POLYGON);
    glVertex2i(600,650);
	  	glVertex2i(1000,650);
    glVertex2i(1000,250);
    glVertex2i(600,250);
    glEnd();
    
    
    
    glColor3ub(165,195,50);
    glBegin(GL_POLYGON);
    glVertex2i(600,450);
	  	glVertex2i(1000,450);
    glVertex2i(1000,0);
    glVertex2i(600,0);
    glEnd();
    
    glColor3ub(245,95,50);
    glBegin(GL_POLYGON);
    glVertex2i(0,450);
	  	glVertex2i(800,450);
    glVertex2i(800,0);
    glVertex2i(0,0);
    glEnd();
    
}



void texti()
{
    
    char string[]="INTRODUCTION";
    void *font=GLUT_BITMAP_TIMES_ROMAN_24;
    int k;
    glColor3f(0.0,0.0,0.0);
    glRasterPos3f(430,600,70);
    for(k=0;k<strlen(string);k++)
        glutBitmapCharacter(font,string[k]);
    
    
    char string1[]="Smart Homes";
    void *font1=GLUT_BITMAP_TIMES_ROMAN_24;
    glColor3f(0.0,0.0,0.0);
    
    
    glRasterPos3f(460,430,0);
    
    for(k=0;k<strlen(string1);k++)
        glutBitmapCharacter(font1,string1[k]);
    
    
    
    char string2[]="BY";
    void *font2=GLUT_BITMAP_TIMES_ROMAN_24;
    glColor3f(0.0,0.0,0.0);
    
    
    glRasterPos3f(700,250+100,0);
    
    for(k=0;k<strlen(string2);k++)
        glutBitmapCharacter(font2,string2[k]);
    
    char string3[]="Prabhjot Singh";
    void *font3=GLUT_BITMAP_HELVETICA_18;
    
    glColor3f(0.0,0.0,0.0);
    
    
    glRasterPos3f(700,220+100,0);
    
    for(k=0;k<strlen(string3);k++)
        glutBitmapCharacter(font3,string3[k]);
    
    
    
    
    
    char string4[]="Rishi Jain";
    void *font4=GLUT_BITMAP_HELVETICA_18;
    
    glColor3f(0.0,0.0,0.0);
    
    
    glRasterPos3f(700,220+70,0);
    
    for(k=0;k<strlen(string4);k++)
        glutBitmapCharacter(font4,string4[k]);
    
    
    
    char string5[]="Under the guidance of ";
    void *font5=GLUT_BITMAP_HELVETICA_18;
    
    glColor3f(0.0,0.0,0.0);
    
    
    glRasterPos3f(60,100,0);
    
    for(k=0;k<strlen(string5);k++)
        glutBitmapCharacter(font5,string5[k]);
    
    char string6[]="Mr. Shasidhar Bola";
    void *font6=GLUT_BITMAP_HELVETICA_18;
    
    glColor3f(0.0,0.0,0.0);
    
    
    glRasterPos3f(60,80,0);
    
    for(k=0;k<strlen(string6);k++)
        glutBitmapCharacter(font6,string6[k]);
    
    
   
    
    char string8[]="Click 'c' to continue ";
    void *font8=GLUT_BITMAP_HELVETICA_18;
    
    glColor3f(0.0,0.0,0.0);
    
    
    glRasterPos3f(670,160,0);
    
    for(k=0;k<strlen(string8);k++)
        glutBitmapCharacter(font8,string8[k]);
    
    
}

void mouse(int btn,int state,int x,int y)
{
    if(btn==GLUT_LEFT_BUTTON && state==GLUT_DOWN)
    {
        scene=1;
        c=0;
        flag=0;
        glutPostRedisplay();
        
    }
    
}
/*- ------------------------------------------------------------------*/


int car_move()
{

    
    if(flag==0)
    {
        x=-150;
        gated();
    }
    
    if(flag==1)
    {
        x+=5;}
        
        
        glPushMatrix();
        glTranslatef(x,0,0);
        car();
        wheel_front();
        glPopMatrix();
        
    
    return x;
}



//static void SpecialKeyFunc( int Key, int x, int y );

static void SpecialKeyFunc( int Key, int x, int y )
{
    flag=0;
    switch ( Key )
    {
        case GLUT_KEY_UP:/*move to right */
            scene=2;
            glutPostRedisplay();
            break;
        case GLUT_KEY_RIGHT:
            scene=1;flag=1;
            glutPostRedisplay();
            break;
    }
}

void keys(unsigned char key, int x, int y)
{
    flag=0;
    if(key=='1')
        scene=1;
   
    if(key=='0')
        scene=0;
    
    if (key=='2')
        scene=2;
    
    if(key=='3')
        scene=3;
    
    if(key=='o')
        scene=4;
    
    if (key=='c') {
        scene=0;
    }
    
    if (key=='4') {
        exit(0);
    }
    
    if (key=='m') {
        scene=0;
    }
    
    if (key=='f') {
        scene=3;
    }
    
    glutPostRedisplay();
    
}

void display(void)
{
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    glOrtho(0, 1000, 10.0, 650,-2000,1500);
   // gluOrtho2D(0,500,0,500);
    glMatrixMode(GL_MODELVIEW);
    
    glClearColor(0.5, 1, 0.5, 0);
    glClear( GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);
    
    if(scene==-1)
    {
        intro();
        texti();
    }
    if (scene==0) {
        menu();
    }
    if (scene==1)
    {
       // sky();
        road2d();
        buildingd();
        treed();
        tree1d();
        tree2d();
        walld();
        text2d();
        textd();
        shrubd();
        shrub1d();
        shrub2d();
        shrub3d();
        shrub4d();
        if(c==0)
            gated();
    
        int v = car_move();
                //flag=1;
        
        if(v>20)
        {
            gateOpen();
        }
   
    }
    
    if(scene==2)
    {
        treeS2_3();
        building2();
        doorInitial();
        faceRec();
        treeS2_1();
        treeS2_2();
        man(x1);
        faceButton();
        
    }
    
    else if(scene==3)
    {
        walls2();
        dine_light2();
        tv();
        remoteZoom();
        clockOff();
        sofa();
    }
    else if(scene==4)
    {
        walls();
        dine_light();
        tv();
        sofa();
        remote2();
        clock();
        tv2();
    }
    glFlush();
    glutSwapBuffers();
}


/**************  main  ***********/
int main(int argc, char **argv)
{
   	glutInit(&argc, argv);
   	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB | GLUT_DEPTH );
   	glutInitWindowSize(1000,1000);
   	glutInitWindowPosition(0,0);
   	glutCreateWindow("Scene1");
   	glutDisplayFunc(display);
    glutMouseFunc(mouse);
   	glutSpecialFunc( SpecialKeyFunc );
    glutKeyboardFunc(keys);

   // glutReshapeFunc(myreshape);
   

    
   	glutMainLoop();
    return 1;
}

