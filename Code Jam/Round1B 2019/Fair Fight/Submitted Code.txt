#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<stdlib.h>
#include<math.h>
#include<malloc.h>
int maximum(int* array, int l, int r)
{
	int i;
	int max = 0;
	for (i = l; i <= r; i++)
	{
		if (max < array[i])
		{
			max = array[i];
		}	
	}
	return max;
}

void CodeJam(int n, int k)
{
	int i, j;
	int l, r;
	int answer = 0;
	int* Ci = (int*)malloc(sizeof(int) * n);
	int* Di = (int*)malloc(sizeof(int) * n);
	for (i = 0; i != n; i++)
	{
		scanf("%d", &Ci[i]);
	}
	for (i = 0; i != n; i++)
	{
		scanf("%d", &Di[i]);
	}
	l = 0;
	r = 0;
	for (i = 0; i < n; i++)
	{
		for (j = i; j < n; j++)
		{
			if (abs(maximum(Ci, i, j) - maximum(Di, i, j)) <= k)
			{
				answer++;
			}
		}
	}
	printf("%d\n", answer);
}
int main()
{
	int i;
	int T;
	scanf("%d", &T);
	for (i = 1; i <= T; ++i)
	{
		printf("Case #%d: ", i);
		int N,K;
		scanf("%d %d", &N,&K);
		CodeJam(N,K);
	}
	return 0;
}