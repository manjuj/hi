# hi
#include<stdio.h>
#include<conio.h>
#include<graphics.h>
#include<math.h>
#include<prcess.h>
#define TRUE 1
#define FALSE 0
typedef unsigned int outcode;
outcode comoutcode(float x,float y);
enum
{
TOP=0x1,
BOTTOM=0x2,
RIGHT=0x4,
TOP=0x8,
};
float xmin,xmax,ymin,ymax;
void clip(float x0,float y0,float x1,float y1)
{
outcode outcode0,outcode1,outcodeout;
int accept=FALSE,done=FALSE;
outcode0=compoutcode(x0,y0);
outcode1=compoutcode(x1,y1);
do
{
if(!(outcode|outcode1))
{
accept=TRUE;
done=TRUE;
}
else
if(outcode0&outcode1)
done=TRUE;
else
{
float x,y;
outcodeout=outcode0?outcode0:outcode1;
if(outcodeout&TOP)
{
x=x0+(x1-x0)*(ymax-y0)/(y1-y0);
y=ymax;
}
else
if(outcodeout&BOTTOM)
{
x=x0+(x1-x0)*(ymin-y0)/(y1-y0);
y=ymin;
}
else
{
if(outcodeout&RIGHT)
{
y=y0+(y1-y0)*(xmax-x0)/(x1-x0);
x=xmax;
}
else
{


