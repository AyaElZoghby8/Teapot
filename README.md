# Teapot
Sold Teapot with OpenGl
#include<windows.h>
#include<GL/glut.h>
float angle=0.5 , rangle=0.5; //Speed Of Rotation
float ROX=0,ROY=1, Tx=0,Ty=0;
void myInit(void)
{
    glClearColor(1,1,1,0);

glColor3f(0.780, 0.768, 0.698);
glOrtho(-44.0,44,-44.0,44,-44.0,44); //not gluOrtho

}
void display(){

glClear(GL_COLOR_BUFFER_BIT);

glRotatef(angle,ROX,ROY,0);
glRotatef(rangle,ROX,ROY,0); //Rotate Around Y-axis
glTranslatef(Tx,Ty,0);


glutSolidTeapot(10);
glFlush();
glutSwapBuffers();
}




 void keyboard (unsigned char key,int x, int y)
 {
     switch(key)
     {
     case 'a':
{
      Tx=Tx+1;

glutPostRedisplay();
        break;}

     case 'b':
      {Ty=Ty-1;

glutPostRedisplay();
        break;
        }




 }}

void mouseClick( int button , int state , int x , int y )
 {

     if ( button == GLUT_RIGHT_BUTTON && state == GLUT_DOWN )
    {

      angle=angle+5;
      ROY=ROY+5;
    glutPostRedisplay();

    }

    if ( button == GLUT_LEFT_BUTTON && state == GLUT_DOWN )
    {
        rangle=rangle-5;
         ROX=ROX-5;

    glutPostRedisplay();

    }

 }


int main(int argc , char **argv)
{
    glutInit(&argc,argv);
glutInitWindowPosition(50, 60);
glutInitWindowSize(800, 800);
glutInitDisplayMode(GLUT_RGB | GL_DOUBLE);//
glutCreateWindow("Teapot");
glutDisplayFunc(display);

glutMouseFunc(mouseClick);
glutKeyboardFunc(keyboard);

//glOrtho(-44.0,44,-44.0,44,-44.0,44); //not gluOrtho

 myInit();
glutMainLoop();
}
