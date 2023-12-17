#include<stdio.h>
void main()
{
int a[10][10],s[10][10],st[10][10];
int i,j,k,r,c;
printf("Enter the no of rows and columns\n");
scanf("%d %d",&r,&c);
printf("Enter the elements\n");
for(i=0;i<r;i++)
{
for(j=0;j<c;j++)
{
scanf("%d",&a[i][j]);
}
}
printf("Sparse Matrix:\n");
for(i=0;i<r;i++)
{
for(j=0;j<c;j++)
{
printf("%d ",a[i][j]);
}
printf("\n");
}
k=1;
for(i=0;i<r;i++)
{
for(j=0;j<c;j++)
{
if(a[i][j]!=0)
{
s[k][0]=i;
s[k][1]=j;
s[k][2]=a[i][j];
k++;
}
}
}
s[0][0]=r;
s[0][1]=c;
s[0][2]=k-1;
printf("Tuple representation of the sparse matrix:\n");
for(i=0;i<k;i++)
{
for(j=0;j<3;j++)
{
printf("%d ",s[i][j]);
}
printf("\n");
}
k=1;
for(i=0;i<s[0][1];i++)
{
for(j=1;j<=s[0][2];j++)
{
if(s[j][1]==i)

{
st[k][0]=s[j][1];
st[k][1]=s[j][0];
st[k][2]=s[j][2];
k++;
}
}
}
st[0][0]=s[0][1];
st[0][1]=s[0][0];
st[0][2]=s[0][2];
printf("Tuple representation of transpose of the sparse matrix:\n");
for(i=0;i<k;i++)
{
for(j=0;j<3;j++)
{
printf("%d ",st[i][j]);
}
printf("\n");
}
printf("Transpose of the Sparse Matrix\n");
k=1;
for(i=0;i<r;i++)
{
for(j=0;j<c;j++)
{
if(i==st[k][0] && j==st[k][1])
{
printf("%d ",st[k][2]);
k++;
}
else
{
printf("0 ");
}
}
printf("\n");
}
