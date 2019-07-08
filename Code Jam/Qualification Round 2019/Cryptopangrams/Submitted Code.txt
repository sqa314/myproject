#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<stdlib.h>
#include<math.h>

void CodeJam(char* p,int n)
{
	int i;
	bool j = false;
	char* answer = (char*)malloc(sizeof(char) * strlen(p));
	for (i = 0; i < strlen(p); i++)
	{
		if (p[i] == 'S')
		{
			answer[i] = 'E';
		}
		else
		{
			answer[i] = 'S';
		}
	}
	for (i = 0; i < strlen(p); i++)
	{
		printf("%c", answer[i]);
	}
	printf("\n");
	free(answer);
}
int main()
{
	int i;
	int t,N;
	scanf("%d", &t);
	for (i = 1; i <= t; ++i)
	{
		scanf("%d", &N);
		char* P = (char*)malloc(sizeof(char) * 50000);
		scanf("%s", P);
		printf("Case #%d: ", i);
		CodeJam(P,N);
		free(P);
	}
	return 0;
}