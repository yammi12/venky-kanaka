                          FLOYDS ALGORITHM

import java.util.Scanner;


public class Floyds_Algorithm {


public static void main(String[] args) {
int wt[][]=new 
int[10][10]; 
int n,i,j;
System.out.println("\nCreate A Graph Using Adjancency Matrix");
System.out.println("\n\nHow Many Vertices are There?:"); 
Scanner in = new Scanner(System.in);
n = in.nextInt();
System.out.println("\n Enter the Elements"); 
System.out.println("[Enter 999 as infinity value]"); 
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
System.out.println("\nwt["+i+"]["+j+"]"); 
wt[i][j]=in.nextInt();
 
}
}
System.out.println("\n\tComputing All Pair Shrotest Path...\n");
Floyd_shortest_path(wt,n);
}
public static void Floyd_shortest_path(int wt[][],int n)
{
int D[][][]= new int[5][10][10];

int i,j,k;
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
D[0][i][j]=wt[i][j];
}
}
for(k=1;k<=n;k++) {
for(i=1;i<=n;i++) {
for(j=1;j<=n;j++) {
D[k][i][j] = min(D[k-1][i][j],(D[k-1][i][k]+D[k-1][k][j]));
}
}
}
for(k=0;k<=n;k++)
{
System.out.println("D("+k+")\t");
for(i=1;i<=n;i++)
 
{
for(j=1;j<=n;j++)
{
System.out.println(""+D[k][i][j]);
}
System.out.println("\n");
}
}
}
public static int min(int a,int b)
{
if(a<b)
return a;
else
}
return b;
}

                               PRIMS ALGORITHM  


import java.util.Scanner;


public class Prims_Algorithm {
static int SIZE = 10;
static int INFINITY = 999;


public static void main(String[] args) { int G[][] = new int[SIZE][SIZE]; int nodes;
int v1,v2,length,i,j,n; System.out.println("\n\tPrim's Algorithm\n");
System.out.println("\nEnter Number of Nodes in The Graph:"); Scanner in = new Scanner(System.in);
nodes = in.nextInt();
System.out.println("\nEnter Number of Edges in The Graph:"); n = in.nextInt();
for(i=0;i<nodes;i++)


for(j=0;j<nodes;j++) G[i][j]=0;
System.out.println("\nEnter Edges and Weights:\n");
for(i=0;i<n;i++) {
System.out.println("\nEnter Edges by V1 and V2:");
 
System.out.println("[Read the Graph From Starting Node 0]:"); v1 = in.nextInt();
v2 = in.nextInt();
System.out.println("\nEnter Corresponding Weight:"); length = in.nextInt();
G[v1][v2] = G[v2][v1]= length;
}
Prim(G,nodes);
}
public static void Prim(int G[][],int nodes) {
int tree[] = new int[SIZE]; int i,j,k;
int min_dist,v1=0,v2=0,total=0;
for(i=0;i<nodes;i++) tree[i]=0;
System.out.println("\n\nThe Minimal Spanning Tree Is:\n"); tree[0]=1;
for(k=1;k<=nodes-1;k++) { min_dist = INFINITY; for(i=0;i<=nodes-1;i++) {
for(j=0;j<=nodes-1;j++) {
if(G[i][j]!=0&&((tree[i]==1&&tree[j]==0)||(tree[i]==0&&tree[j]==1))) {
if(G[i][j]<min_dist) { min_dist = G[i][j]; v1 = i;
v2 = j;
}}}}
System.out.println("\nEdge["+v1+","+v2+"]and Weight"+min_dist);
tree[v1] = tree[v2]=1; total = total+min_dist;
}
System.out.println("\n\n\tTotal Path Length Is = "+total);
}}



                        TRAVELLING SALES MAN

import java.util.Scanner;


public class Travelling_Sales_Person_Problem {
static int cost=0;


public static void main(String[] args) {
int a[][] = new int[10][10]; int visited[] = new int[10]; int n;
System.out.println("\n Enter No.of Cities:"); Scanner in = new Scanner(System.in);
n = in.nextInt();
create(a,visited,n); System.out.println("\n\nThe Path is:"); mincost(a,n,0,visited);
 
display();
}
public static void create(int a[][], int visited[],int n)
{
int i,j;
System.out.println("\nEnter Cost Matrix:");
for(i=0;i<n;i++) {
System.out.println("Row#:"+(i+1));
for(j=0;j<n;j++)
{
Scanner sc = new Scanner(System.in); a[i][j]=sc.nextInt();

}
visited[i]=0;
}
System.out.println("\n\nThe Cost Matrix is	");
for(i=0;i<n;i++)
{
System.out.println("\n");
for(j=0;j<n;j++)
System.out.println(""+a[i][j]);
}
}
public static void mincost(int a[][],int n,int city,int visited[])
{
int i,city_no;
 
visited[city]=1; System.out.println((city+1)+"-->"); city_no=least(a,visited,n,city); if(city_no==999)
{
city_no=0; System.out.println(""+(city_no+1)); cost+=a[city][city_no];
return;
}
mincost(a,n,city_no,visited);
}


public static int least(int a[][],int visited[],int n,int c)
{
int i,min_node=999;
int min = 999,New_min = 0;
for(i=0;i<n;i++)
{
if((a[c][i]!=0)&&(visited[i]==0)) if(a[c][i]<min) {
min=a[i][0]+a[c][i]; New_min = a[c][i]; min_node = i;
}
}
if(min!=999)
 
cost+=New_min;
return min_node;
}
public static void display()
{
System.out.println("\n\nThe Cost of Tour:"+cost);
}}
                        
