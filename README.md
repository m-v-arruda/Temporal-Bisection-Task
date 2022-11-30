# Temporal-Bisection-Task
This is the script used to analise the temporal bisection task data extracted from the JATOS platform. 
The temporal bisection task was developed using the OpenSesame software, the task was designed to be run online, so that the temporal bisection task collection can be done remotely.
The "Example .csv file" is an example of a file extracted from the JATOS platform that was converted form .txt to .csv with the use of the OSWeb tool available in the OpenSesame software.
The "Graph Example" is a result from the code that is available. 
Also in the code, it is possible to extract the Bisection Point, the Differential Threshold (Difference Limen) and the Weber's Ratio from a participant.


APPENDIX I - Algorithm

(Article DOI)

The psychometric function, its graphs, the BP, DT, and WR were obtained with custom-made python 3.8 routines, using the Google Colab platform. The data obtained by the JATOS platform were converted to .csv format using the OSWeb tool of the OpenSesame software. Then the .csv spreadsheet containing the participants 'short' and 'long' responses was imported into Google Colab using the pandas library. We also used the NumPy, matplotlib.pyplot, and scipy.optimize libraries. 

We computed the probability of responding long Pℓ(T) using only the 70 test trials from Phase 3. For each interval, the probability was computed as the ratio between the number of long responses and the total number of responses. This is automatically computed with the crosstab routine from pandas. The fraction of 'short' or 'long'  responses for each of the stimulus durations is stored in the perc_answer variable. 
We fitted a sigmoid function to the  presented stimuli (time_stm) as a function of Pℓ (perc_long). The sigmoid curve was defined as: 

f(x) = 1(1 + e-a*(x-BP)) .				(i)

We used the curve_fit routine from scipy.optimize package to fit the curve, obtaining the optimized parameters  (BP, DT and WR). The BP is equal to parameter b.
We obtained the differential threshold by calculating the intervals T1(Pℓ=0,25) and T2(Pℓ=0,75) directly from a and b: 

T1= b -  log(3)a   (ii)
T2= b +  log(3)a  (iii)

The Weber ratio was calculated as (T2 - T1) / BP.
