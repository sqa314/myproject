#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<stdlib.h>
#include<math.h>
#include<malloc.h>

void CodeJam(int p, int q)
{
	int i, j, k;
	int answer = 0;
	int minx = q;
	int miny = q;
	int max = 0;
	int** location = (int**)malloc(sizeof(int*) * (q + 1) * (q + 1));
	int* x = (int*)malloc(sizeof(int) * p);
	int* y = (int*)malloc(sizeof(int) * p);
	char* c = (char*)malloc(sizeof(char) * p);
	for (i = 0; i != p; i++)
	{
		scanf("%d %d %c", &x[i], &y[i], &c[i]);
	}
	for (i = 0; i != q+1; i++)
	{
		location[i] = (int*)malloc(sizeof(int*) * (q+1));
	}
	for (i = 0; i != q+1; i++)
	{
		for (j = 0; j != q+1; j++)
		{
			location[i][j] = 0;
		}
	}
	for (k = 0; k != p; k++)
	{
		switch (c[k])
		{
		case 'S':
			for (i = 0; i != y[k]; i++)
			{
				for (j = 0; j != q+1; j++)
				{
					location[i][j]++;
				}
			}
			break;
		case 'N':
			for (i = y[k]+1; i != q+1; i++)
			{
				for (j = 0; j != q+1; j++)
				{
					location[i][j]++;
				}
			}
			break;
		case 'E':
			for (i = 0; i != q+1; i++)
			{
				for (j = x[k]+1; j != q+1; j++)
				{
					location[i][j]++;
				}
			}
			break;
		case 'W':
			for (i = 0; i != q+1; i++)
			{
				for (j = 0; j != x[k]; j++)
				{
					location[i][j]++;
				}
			}
			break;
		}
	}
	for (i = 0; i != q + 1; i++)
	{
		for (j = 0; j != q + 1; j++)
		{
			if (max < location[i][j])
			{
				max = location[i][j];
			}
		}
	}
	for (i = 0; i != q+1; i++)
	{
		for (j = 0; j != q+1; j++)
		{
			if (location[i][j] == max)
			{
				if(minx > j)
				{
					minx = j;
				}
				if(miny > i)
				{
					miny = i;
				}
			}
		}
	}
	printf("%d %d\n", minx, miny);
}
int main()
{
	int i;
	int T;
	scanf("%d", &T);
	for (i = 1; i <= T; ++i)
	{
		printf("Case #%d: ", i);
		int P, Q;
		scanf("%d %d", &P, &Q);
		CodeJam(P, Q);
	}
	return 0;
}