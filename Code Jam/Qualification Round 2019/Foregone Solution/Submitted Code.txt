#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<string.h>
#include<stdbool.h>
#include<stdlib.h>
#include<math.h>

void CodeJam(char* n)
{
	int i;
	bool j = false;
	char* answer1 = (char*)malloc(sizeof(char) * strlen(n));
	char* answer2 = (char*)malloc(sizeof(char) * strlen(n));
	for (i = 0; i < strlen(n); i++)
	{
		if (n[i] != '4')
		{
			answer1[i] = n[i];
			answer2[i] = '0';
		}
		else
		{
			answer1[i] = '2';
			answer2[i] = '2';
		}
	}
	for (i = 0; i < strlen(n); i++)
	{
		printf("%c", answer1[i]);
	}
	printf(" ");
	for (i = 0; i < strlen(n); i++)
	{
		if (!j)
		{
			if (answer2[i] != '0')
			{
				j = true;
			}
		}
		if (j)
		{
			printf("%c", answer2[i]);
		}
	}
	printf("\n");
	free(answer1);
	free(answer2);
}
int main()
{
	int i;
	int t;
	scanf("%d", &t);
	for (i = 1; i <= t; ++i)
	{
		char* N = (char*)malloc(sizeof(char) * 100);
		scanf("%s", N);
		printf("Case #%d: ", i);
		CodeJam(N);
		free(N);
	}
	return 0;
}