# DistributionsDemo
Demonstrating and exploring random number distributions in Dyalog APL

DistributionsDemo is code I use at the Dyalog 2021 conference to demonstrate the Dyalog APL code for sampling random number distributions. It also includes functions for displaying probability density graphs and cummulative distribution graphs for all the implemented random number distributions as well for calculating Kolmogorov-Smirnov statistics.

## Creating the DistributionDemo Workspace

First clone this repository to a local directory -- say c:\DistributionDemo.

Then, in a clear workspace connect that directory with the # namespace by

    ]link.import # c:\DistributionDemo\Source -source=dir

You should now have a namespace called Demo. That namespace contains the code I used for my presentation called 

    "QA for Statistical Distributions in Dyalog V18.2"

If you also want access to distributions from the R programming environment, you'll need to install Kimmo Linna's RSConnect system from https://github.com/kimmolinna/rsconnect.git. 

Follow Kimmo's instructions for installing R, and then install his RsConnect interface by

1. Clone his repository to a directory, say c:\kimmo-rsconnect

2. Install his #.RS namespace by

      ]load c:\kimmo-rsconnect\rserve.dyalog

Then you will have access to the R distributions I used in the presentation. You'll also be able execute expressions in the R environment, and you will able to send data to R from APL as well getting data from R to APL.

## Final Set-up Steps

When you're using the demonstration workspace, most of the time you'll want to be located within the Demo namespace, and you'll usually want to start with a clean state. To that end, set a ⎕LX expression like this:

      ⎕LX←'#.Demo.Reset ⋄ ⎕CS''#.Demo'''

Then save your workspace with a name you'll recognize!

## Functions in the Demo Namespace

DistNames -- returns a  list of the distribution names

Use ↑DistNames ⍝ to see those names in a matrix

ShowPDFs -- Draws a probability density graph for a given distribution with a specific set of parameters.

For Example:  2 5 ShowPDFs 'Beta'

For Example:  { XSpan←0 2.5 ⋄ (1 1.5 5,¨1 1 1) ShowPDFs 'Weibull'}⍬

will draw a graph of the probability density function for the Beta distribution with the parameters 2 5. The actual sampled distribution will be drawn with a color and will be superimposed over a black line showing the ideal curve for the pdf function.

ShowCDFs -- Draws the normalized cumulative probability density function for a distribution with a specific set of parameters. As with ShowPDFs, the CDF curve for the actual samples will be drawn in color, and the ideal CDF curve will be drawn in black.

For Example: 2 5 ShowCDFs 'Beta'

ShowLogPDFs -- Draws the PDF graph on a logarithmic Y axis. 

For Example: 2 5 ShowLogPDFs 'Beta'

KS_Statistic -- Calculates a Kolmogorov-Smirnov statistic comparing the normalized CDF curves for the actual samples against the ideal CDF curve.

For Example: 2 5 KS_Statistic 'Beta'

TestDistributions -- Runs a set of KS comparisons for all the distributions with a selected set of control parameters, and reports any tests which has a KS statistic which is beyond a failure threshold.

For Example:  TestDistributions ⍬ ⍝ Runs all the tests.

For Example:  TestDistributions 10 ⍝ Runs a random subset of 10 tests.

QAResults -- A function used by TestDistributions. It does the sampling and calculates KS statistics while the TestDistributions function looks for tests which exceed the failure threshold.