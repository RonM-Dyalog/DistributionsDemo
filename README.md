# DistributionsDemo
Demonstrating and exploring random number distributions in Dyalog APL

DistributionsDemo is code I use at the Dyalog 2021 conference to demonstrate the Dyalog APL code for sampling random number distributions. It also includes functions for displaying probability density graphs and cummulative distribution graphs for all the implemented random number distributions as well for calculating Kolmogorov-Smirnov statistics.

## Creating the DistributionDemo Workspace

First clone this repository to a local directory -- say c:\DistributionDemo.

Then, in a clear workspace connect that directory with the # namespace by

    ]link.create # c:\DistributionDemo\Source -source=dir

Then disconnect the link connection by

    ]link.break #

You should now have a namespace called Demo. That namespace contains the code I used for my presentation called 

    "QA for Statistical Distributions in Dyalog V18.2"

If you also want access to distributions from the R programming, you'll need to install Kimmo Linna's RSConnect system from https://github.com/kimmolinna/rsconnect.git. 

Follow Kimmo's instructions for installing R, and then install his RsConnect interface by

1. Clone his repository to a directory, say c:\kimmo-rsconnect

2. Install his #.RS namespace by

      ]load c:\kimmo-rsconnect\rserve.dyalog

Then you will have access to the R distributions I used in the presentation. You'll also be able execute expressions in the R environment, and you will able to send data to R from APL as well getting data from R to APL.

Oh! And before we forget, save your workspace with a name you'll recognize!