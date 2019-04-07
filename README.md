# 2
#include <stdio.h>
#include <conio.h>
#include <time.h>


int main(int argc, char *argv[])
{
    int M[3][3];
    int *i, j, k, cflag, n;
    int sum1, sum2, rsum[3], csum[3], stdsum;
    
    int resultCount, totalCount, partResultCount;
    clock_t t_start;

    t_start = clock();
    n = 3;
    stdsum = 15;
    resultCount = totalCount = partResultCount = 0;

    i = &(M[0][0]);
   

    for (i[0] = 1; i[0] <= 9; i[0]++)
    {
        for (i[1] = 1; i[1] <= 9; i[1]++)
        {
            if (i[1] == i[0])
                continue;
            for (i[2] = 1; i[2] <= 9; i[2]++)
            {
                if (i[2] == i[1] || i[2] == i[0])
                    continue;
                for (i[3] = 1; i[3] <= 9; i[3]++)
                {
                    if (i[3] == i[2] || i[3] == i[1] || i[3] == i[0])
                        continue;
                    for (i[4] = 1; i[4] <= 9; i[4]++)
                    {
                        if (i[4] == i[3] || i[4] == i[2] || i[4] == i[1] || i[4] == i[0])
                            continue;
                        for (i[5] = 1; i[5] <= 9; i[5]++)
                        {
                            if (i[5] == i[4] || i[5] == i[3] || i[5] == i[2] || i[5] == i[1] || i[5] == i[0])
                                continue;
                            for (i[6] = 1; i[6] <= 9; i[6]++)
                            {
                                if (i[6] == i[5] || i[6] == i[4] || i[6] == i[3] || i[6] == i[2] || i[6] == i[1] || i[6] == i[0])
                                    continue;
                                for (i[7] = 1; i[7] <= 9; i[7]++)
                                {
                                    if (i[7] == i[6] || i[7] == i[5] || i[7] == i[4] || i[7] == i[3] || i[7] == i[2] || i[7] == i[1] || i[7] == i[0])
                                        continue;
                                    for (i[8] = 1; i[8] <= 9; i[8]++)
                                    {
                                        if (i[8] == i[7] || i[8] == i[6] || i[8] == i[5] || i[8] == i[4] || i[8] == i[3] || i[8] == i[2] || i[8] == i[1] || i[8] == i[0])
                                            continue;

                                        totalCount++;
                                        // 初始化各求和变量，准备求和检查
                                        for (j = 0; j < 3; j++)
                                        {
                                            csum[j] = 0;
                                            rsum[j] = 0;
                                        }
                                        sum1 = 0;
                                        sum2 = 0;

                                        // 按行/列、对角线求和
                                        for (j = 0; j < 3; j++)
                                        {
                                            for (k = 0; k < 3; k++)
                                            {
                                                csum[k] += M[j][k];
                                                rsum[j] += M[j][k];
                                            }
                                            sum1 += M[j][j];
                                            sum2 += M[j][2 - j];
                                        }

                                        // 检查对角线是否相等
                                        if (sum1 != stdsum || stdsum != sum2)
                                            continue;

                                        partResultCount++;
                                        // 检查是否满足各行各列相等
                                        cflag = 0;
                                        for (j = 0; j < 3; j++)
                                        {
                                            if (csum[j] != stdsum || rsum[j] != stdsum)
                                            {
                                                cflag = 1;
                                                break;
                                            }
                                        }

                                        
                                        if (cflag == 0)
                                        {
                                            resultCount++;

                                            printf("[%d] [%d] [%d] \t\tms elapsed:[%ld]\r\n", totalCount, partResultCount, resultCount, clock() - t_start);
                                            for (j = 0; j < 3; j++)
                                            {
                                                for (k = 0; k < 3; k++)
                                                {
                                                    printf("%d ", M[j][k]);
                                                }
                                                printf("\n");
                                            }
                                            printf("\n");
                                        }
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    }

    _getch();
}
