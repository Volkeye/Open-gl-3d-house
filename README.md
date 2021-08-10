# Open-gl-3d-house
#include<GL/glut.h>
#include<math.h>



void timer (int);
void reshape (int,int);

float angle =0.0;
 void myinit(void)
  {
 glClearColor(1.0,1.0,1.0,0.0);
 glMatrixMode(GL_PROJECTION);
 glLoadIdentity();
 glTranslatef(0.9,0.0,-8.0 );
 glRotatef (angle,1.0,0.0,0.0);
 glRotatef (angle,0.0,1.0,0.0);
 glRotatef (angle,0.0,1.0,1.0);
 glEnable(GL_DEPTH_TEST);
}
void reshape(int w,int h)
{
    glViewport(0,0,w,h);
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    glMatrixMode(GL_MODELVIEW);

}

void timer(int){
	glutPostRedisplay();
	glutTimerFunc(1000/60,timer,0);
	
	angle+=0.8;
	if(angle>360)
	angle=angle-360.0;
}

 
 void hut(void)
 {
glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT);
glColor3f(0.0,0.4,0.2);

		glBegin(GL_QUADS);
		glVertex3f (0.1, 0.1, 0.0);
        glVertex3f (0.4, 0.1, 0.0);
        glVertex3f (0.4, 0.5, 0.0);
        glVertex3f (0.1, 0.5, 0.0); 
    glEnd();
glColor3f(1.0,1.0,0.0);

		glBegin(GL_POLYGON);
		glVertex3f (0.10, 0.5, 0.3);
        glVertex3f (0.4, 0.5, 0.0);
        glVertex3f (0.25, 0.75, 0.0);
       glEnd();
glColor3f(0.0,1.0,0.0);

		glBegin(GL_QUADS);
		glVertex3f (0.4, 0.1, 0.0);	
        glVertex3f (0.8, 0.4, 0.0);
        glVertex3f (0.8, 0.75, 0.0);
        glVertex3f (0.4, 0.5, 0.0);
    glEnd();
glColor3f(0.4,0.0,0.4);

		glBegin(GL_QUADS);
		glVertex3f (0.4, 0.5, 0.0);
        glVertex3f (0.8, 0.75, 0.0);
        glVertex3f (0.62, 0.93, 0.0);
        glVertex3f (0.25, 0.75, 0.0);
    glEnd();
    
glColor3f(0.6,0.3,0.4);
		glBegin(GL_QUADS);
		glVertex3f (0.1, 0.5, 0.4);
        glVertex3f (0.4, 0.75, 0.8);
        glVertex3f (0.0, 0.9, 0.6);
        glVertex3f (0.0, 0.7, 0.2);
    glEnd();
glFlush();
}
int main(int argc,char** argv)
{
glutInit(&argc,argv);
glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB|GLUT_DEPTH);
glutInitWindowPosition(200,200);
glutInitWindowSize(700,500);
glutCreateWindow("simple house 2");
glutTimerFunc(0,timer,0);
glutReshapeFunc(reshape);
myinit();
glutDisplayFunc(hut);
glutMainLoop();
}






