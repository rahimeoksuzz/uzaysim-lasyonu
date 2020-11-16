from OpenGL.GL import *
from OpenGL.GL import glBegin
from OpenGL.GLUT import *
from OpenGL.GLU import *
import time
import sys

yıl = 0
gün = 0

start_time = time.time() #Zamanlama işlemi yapmak için

def InitGL():
    glClearColor(0.0, 0.0, 0.0, 0.0)
    glMatrixMode(GL_PROJECTION)
    glLoadIdentity()
    gluOrtho2D(-5.0, 5.0, -5.0, 5.0)
    glMatrixMode(GL_MODELVIEW)

def drawAxis():
    #Bu fonksiyon x ve y eksenlerini nokta şeklinde çizdiriyor.
    glColor3f(0, 1, 1)
    for i in range(-5, 5):
        glBegin(GL_POINTS)
        glVertex2f(i, 0)
        glVertex2f(0, i)
        glEnd()

def DrawGLScene():
    #ay dünya ve güneş oluşturduğumuz kısım
    yıl = ((time.time() - start_time) / 30.0) #yılı simüle etmek için 6 saniye
    gün = 365 * yıl

    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT)

    glColor3f(1.0, 1.0, 0.0)
    glPushMatrix()
    glutSolidSphere(1.0, 20, 20)  #güneş
    glRotatef(yıl * 360.0, 0.0, 1.0, 0.0)  #güneş dönderiliyor
    glTranslatef(3.0, 0.0, 0.0) #güneş bu konuma taşınıyor

    glPushMatrix()

    glPushMatrix()
    glRotatef(gün * 360.0, 0.0, 1.0, 0.0)  #dünya dönderiliyor
    glColor3f(0, 0, 1)
    glutSolidSphere(0.3, 10, 20) #dünya
    glPopMatrix()

    glPushMatrix()
    glRotatef((365 / 27.3) * yıl * 360.0, 0.0, 1.0, 0.0)  #ay dönderiliyor
    glTranslatef(1.0, 0.0, 0.0)  #ay bu konuma taşınıyor
    glColor3f(1.0, 1.0, 1.0)
    glutSolidSphere(0.1, 10, 20)  #ay
    glPopMatrix()

    glPopMatrix()
    glPopMatrix()
    drawAxis()
    glutSwapBuffers()

def main():
    glutInit()
    glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE)
    glutInitWindowSize(1000, 1000)
    glutInitWindowPosition(100, 100)
    glutCreateWindow("UZAY SIMULASYONU")
    InitGL()
    glutDisplayFunc(DrawGLScene)
    glutIdleFunc(DrawGLScene)
    glutMainLoop()

main()
