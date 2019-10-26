# utl-Othogonal-Full-Factorial-Design-Matrix
Othogonal Full Factorial Design Matrix

    Othogonal Full Factorial Design Matrix

    github
    https://github.com/rogerjdeangelis/utl-Othogonal-Full-Factorial-Design-Matrix

    Inspired by
    https://communities.sas.com/t5/SAS-IML-Software-and-Matrix/Proc-IML-Full-Factorial-Matrix/m-p/599458

    More complete example
    http://rstudio-pubs-static.s3.amazonaws.com/42659_4e651814469d4e36b04d230426824150.html

    Problem: Create the follwing 2^3 design matri such tjat

          X1 X2 X3
        1 -1 -1 -1
        2  1 -1 -1
        3 -1  1 -1
        4  1  1 -1
        5 -1 -1  1
        6  1 -1  1
        7 -1  1  1
        8  1  1  1

      Where

       sum(x1*x2)=0
       sum(x1*x3)=0
       sum(x2*x3)=0

     These types of designs can lead to regressions where parameter estimates
     are independent of each other(othogonal). I believe Fourier Analysis and Polynomial
     regression can have this property.

    Solution:

    %utl_submit_r64('
    library(AlgDesign);
    levels.design = c(2,2,2);
    D <- gen.factorial(levels.design);
    D;
    str(D);
    dx1x2<-sum(D$X1*D$X2);
    dx1x3<-sum(D$X1*D$X3);
    dx2x3<-sum(D$X2*D$X3);
    dx1x2;
    dx1x3;
    dx2x3;
    ');

    log

     X1 X2 X3
     -1 -1 -1
      1 -1 -1
     -1  1 -1
      1  1 -1
     -1 -1  1
      1 -1  1
     -1  1  1
      1  1  1
    data.frame':	8 obs. of  3 variables:
    $ X1: num  -1 1 -1 1 -1 1 -1 1
    $ X2: num  -1 -1 1 1 -1 -1 1 1
    $ X3: num  -1 -1 -1 -1 1 1 1 1
    1] 0
    1] 0
    1] 0


