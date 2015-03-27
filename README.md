# Parcial

#include <GL/gl.h>
#include <GL/glut.h>
#include <stdlib.h>


double radius=50 ,slices=50, stacks=40;
double base=10, height=20, slices2=10, stacks2=10;




void reshape(int w, int h)
{
glViewport(0, 0, (GLsizei) w, (GLsizei) h);
// Activamos la matriz de proyeccion.
glMatrixMode(GL_PROJECTION);
// "limpiamos" esta con la matriz identidad.
glLoadIdentity();
// Usamos proyeccion ortogonal
glOrtho(-300, 300, -300, 300, -300, 300);
// Activamos la matriz de modelado/visionado.
glMatrixMode(GL_MODELVIEW);
// "Limpiamos" la matriz
glLoadIdentity();
 
}

void figuras(void)
{
// "Limpiamos" el frame buffer con el color de "Clear", en este
// caso negro.
glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
glMatrixMode( GL_MODELVIEW_MATRIX );
glLoadIdentity();

glFlush();

}

void keyboard(unsigned char key, int x, int y)
{
switch (key)
{
case '1': 


glScalef(1,1,1);
// Rotacion de 25 grados en torno al eje x
glRotated(25.0, 1.0, 0.0, 0.0);
// Rotacion de -30 grados en torno al eje y
glRotated(-30.0, 0.0, 1.0, 0.0);

// Dibujamos 
glPushMatrix();

//setMaterial

glutWireSphere(50,50,40);

break;
case '2': 

glScalef(1,1,1);
// Rotacion de 25 grados en torno al eje x
glRotated(25.0, 1.0, 0.0, 0.0);
// Rotacion de -30 grados en torno al eje y
glRotated(-30.0, 0.0, 1.0, 0.0);

//setMaterial
glutWireCone(10,20,10,10);

break;
case '3': 

glScalef(1,1,1);
// Rotacion de 25 grados en torno al eje x
glRotated(25.0, 1.0, 0.0, 0.0);
// Rotacion de -30 grados en torno al eje y
glRotated(-30.0, 0.0, 1.0, 0.0);

// Dibujamos
glPushMatrix();

//setMaterial

glutWireCube(100);

case 27: // 27 es Esc
exit(0); // Sale del programa
}
glutPostRedisplay(); // actualización de visualización
}
int main(int argc, char **argv)
{
// Inicializo OpenGL
glutInit(&argc, argv);
// Activamos buffer simple y colores del tipo RGB
glutInitDisplayMode (GLUT_RGB | GLUT_DEPTH);
// Definimos una ventana de medidas 800 x 600 como ventana
// de visualizacion en pixels
glutInitWindowSize (800, 600);
// Posicionamos la ventana en la esquina superior izquierda de
// la pantalla.
glutInitWindowPosition (0, 0);
// Creamos literalmente la ventana y le adjudicamos el nombre que se
// observara en su barra de titulo.
glutCreateWindow ("Tetera");
// Inicializamos el sistema

glutDisplayFunc(figuras);
glutReshapeFunc(reshape);
glutKeyboardFunc(keyboard); //llama funcion teclado
glutMainLoop();
// glutponerMaterialFunc(ponerMaterial);
return 0;
}
