# Temporal Bisection Task

This is the script used to analise the temporal bisection task data extracted from the _JATOS_ platform. 
The temporal bisection task was developed using the _OpenSesame_ software, the task was designed to be run online, so that the temporal bisection task collection can be done remotely.
The "Example _.csv_ file" is an example of a file extracted from the JATOS platform that was converted form .txt to .csv with the use of the _OSWeb_ tool available in the _OpenSesame_ software.
The "Graph Example" is a result from the code that is available. 
Also in the code, it is possible to extract the **Bisection Point**, the **Differential Threshold** (Difference Limen) and the **Weber's Ratio** from a participant.


## APPENDIX I - Algorithm

(_Appendix in construction..._)

The psychometric function, its graphs, the BP, DT, and WR were obtained with custom-made python 3.8 routines, using the _Google Colab_ platform. The data obtained by the _JATOS_ platform were converted to _.csv_ format using the _OSWeb_ tool of the _OpenSesame_ software. Then the .csv spreadsheet containing the participants 'short' and 'long' responses was imported into Google Colab using the pandas library. We also used the _NumPy_, _matplotlib.pyplot_, and _scipy.optimize_ libraries. 

We computed the probability of responding long P<sub>ℓ</sub>(T) using only the 70 test trials from Phase 3. For each interval, the probability was computed as the ratio between the number of long responses and the total number of responses. This is automatically computed with the crosstab routine from pandas. The fraction of '_short_' or '_long_'  responses for each of the stimulus durations is stored in the _perc_answer_ variable. 
We fitted a sigmoid function to the  presented stimuli (_time_stm_) as a function of P<sub>ℓ</sub> (perc_long). The sigmoid curve was defined as: 

$$ f(x) = {{1} \over {1 + e^{-a*(x-BP)}}} $$

We used the _curve_fit_ routine from _scipy.optimize_ package to fit the curve, obtaining the optimized parameters  (BP, DT and WR). The BP is equal to parameter _b_.
We obtained the differential threshold by calculating the intervals T1(P<sub>ℓ</sub>=0,25) and T2(P<sub>ℓ</sub>=0,75) directly from _a_ and _b_: 

$$ T1 = {b -  {log(3)} \over {a} }$$

$$ T2 = {b +  {log(3)} \over {a} }$$

The *Weber's ratio* (WR) was calculated as:

$$ WR = {{(T2 - T1)} \over BP} $$
