#include <stdio.h>
#include <math.h>
double ln(double x, int p) { 
    double y = 0;
    int sign = 1;
    for (int i = 1; i < p; i++) {
        y += sign * pow(x, i)/i;
        sign *= -1;  
    }
    return y;
}
int main()
{
    double precision = 0.01, count = 10; 
    double etalon, taylor, delta; 
        for (double i = -0.5; i < 0.5; i += 0.1) {
        etalon = log(1+i);
        taylor = ln(i, count);
        delta = fabs(etalon - taylor);
        if (delta > precision) {  
            return 1;
        }
    }
        return 0; 
}
