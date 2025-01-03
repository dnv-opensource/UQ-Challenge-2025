<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

# The NASA and DNV Challenge on Optimization Under Uncertainty  
<p align="center">
    <img src="./assets/NASA-Logo-Large.png" alt="NASA Logo" height="150" />
    <img src="./assets/DNV_logo_RGB.png" alt="DNV Logo" height="150" />
</p>

The 2025 UQ Challenge presents a problem designed to bring researchers together to tackle a problem common to many complex real-world systems. 

The challenge will run from January 6th to March 31st, 2025, and accepted responses will be part of a special session at the [ESREL 2025 conference](https://esrel2025.com/) in Stavanger, Norway, from June 15th to 19th. The information needed to take part in the challenge is given below.  

## Table of Contents
- [Motivation](#motivation)
- [Register for the 2025 UQ Challenge](#register-for-the-2025-uq-challenge)
- [Timeline](#timeline)
- [Problem description](#problem-description)
- [How to access the local computational model](#how-to-access-the-local-computational-model)
- [How to generate data from the real system](#how-to-generate-data-from-the-real-system)
- [How to submit numerical results](#how-to-submit-numerical-results)
- [Questions and Answers](#questions-and-answers-updated-as-new-questions-arrive)

## Motivation
NASA missions often involve the development of new vehicles and systems that must be designed to operate in harsh domains with a wide array of operating conditions. Similarly, DNV works to safeguard life, property, and the environment across a range of industries by ensuring that complex engineered systems can be trusted to operate reliably, even during rare and extreme events. DNV collaborates across various sectors to address the challenges of designing and operating safety-critical systems.

Both NASA and DNV deal with high-consequence and safety-critical systems for which quantitative data is either very sparse or prohibitively expensive to collect. Limited heritage data may exist, but is also usually sparse and may not be directly applicable to the system of interest, making Uncertainty Quantification (UQ) extremely challenging.

Recognizing the shared challenges in UQ across different sectors, NASA Langley Research Center and DNV Group Research and Development have developed a challenge problem to unite a community of researchers toward common goals. While the problem formulation is presented in a discipline-independent framework, the underlying application is consistent with the complexities of realistic systems. This collaborative effort aims to advance methodologies in UQ that are broadly applicable, enhancing safety and reliability across various domains.

This challenge aims to advance research within:
- Modeling and refinement of uncertainty given sparse data
- Propagation of mixed aleatory and epistemic uncertainties through system models
- Design optimization in the presence of uncertainty

## Register for the 2025 UQ Challenge
Each participating group should first register by sending an email to [uqchallenge@dnv.com](mailto:uqchallenge@dnv.com) including the name of all the participants, their email addresses, and affiliations. Please also indicate who will be the point of contact for the group.

Accepted responses to the challenge will be part of a dedicated session of the [ESREL 2025 conference](https://esrel2025.com/) to be held in Stavanger, Norway, from 15-19 June 2025. Registration to the conference is done separately through the conference website.

## Timeline
- **December 27th:** Deadline for registering new teams  
- **January 6th:** Start of challenge. Access to simulation models and data will be opened.  
- **March 17th:** First paper deadline. We aim to review and provide feedback to each team within 1 week (by March 24th).  
- **March 31st:** Deadline for submitting numerical results. See [How to submit numerical results](#how-to-submit-numerical-results).
- **April 10th:** Deadline for camera-ready paper.

See also [https://esrel2025.com/](https://esrel2025.com/) for deadlines regarding conference registration.

## Problem description
The official problem description can be found on the NASA website [here](https://uqtools.larc.nasa.gov/the-nasa-and-dnv-challenge-on-optimization-under-uncertainty/).

Some additional details for Problem 2: Design optimization
- The system outputs in $$I_1$$ corresponds to outputs $$(y_1, y_2, y_3)$$ from the simulation model and the outputs in $$I_2$$ corresponds to outputs $$(y_4, y_5, y_6)$$. Furter information about the format of the output data is provided in the sections below. 
- For the limit state functions, the constants $$c_i$$ are set to $$c_1 = 2750, c_2 = 2000, c_3 = 1000$$. 

## How to access the local computational model 
**Link to local simulation model:** Can be downloaded [here](https://github.com/dnv-opensource/UQ-Challenge-2025/releases/tag/0.0.2)

The simulation model will take as input a vector $$\textbf{X} = (\textbf{X}_a, \textbf{X}_e, \textbf{X}_c, \omega)$$
 consisting of aleatory, epistemic, and control variables with dimensionalities $$n_a = 2$$, $$n_e = 3$$, and $$n_c = 3$$, respectively. Additionally, there is an aleatory variable $$\omega$$ representing the random seed.

The local model will be provided as a 'black box' compiled binary. An example of how to run this model is provided for [Python](USING_LOCAL_MODEL_PYTHON.md) and [MATLAB](USING_LOCAL_MODEL_MATLAB.md).

To test your setup before the challenge is launched, you can download a "dummy" model available [here](https://github.com/dnv-opensource/UQ-Challenge-2025/releases/tag/0.0.1). This takes as input a vector of the same format as the "real" model and returns an array of the correct shape but with only zeros.

## How to generate data from the real system
Each participating team will get access to an online solution for generating (synthetic) data from the real system with the control parameter $$X_c$$ they specify. 
The simulation budget for each team is set to N=10, which means you can generate data for 10 different sets of control parameters. For each simulation call for a set of control parameters, the model will generate K=100 samples. Please read section 4.1 in the [problem description](https://uqtools.larc.nasa.gov/the-nasa-and-dnv-challenge-on-optimization-under-uncertainty/) for further details regarding the simulation budget 

<p align="center">
    <img src="./assets/DefaultProject.png" alt="STC" height="150" />
    <img src="./assets/SimulationsPage_cropped.png" alt="sim cropped" height="150" />
</p>

To access this solution: 
1) Create an account on the Simulation Trust Center (STC) as explained [here](CREATING_STC_ACCOUNT.md).
2) Access the UQ Challenge project and run experiments as explained [here](USING_STC.md).

**Note:** We have included an [example output file](https://github.com/dnv-opensource/UQ-Challenge-2025/blob/main/Y_out_example.csv) from the real system, which you can use for analysis before you have completed the setup of your account to run experiments yourself. For this dataset, we have used the initial baseline design $$X_c = [0.533, 0.666, 0.5]$$.

Please follow this [tutorial](https://github.com/dnv-opensource/UQ-Challenge-2025/blob/main/POSTPROCESS_STC_RESULTS.md) for information on how to post-process these output files. 

## How to submit numerical results
To submit the numerical results, please see the example in [results_template](https://github.com/dnv-opensource/UQ-Challenge-2025/tree/main/results_template). 

The UMs should be submitted through csv files with generated samples. Everything else can be included in the provided results.json file. 

## Questions and Answers (updated as new questions arrive)
Answers to any questions we receive that are relevant for all respondents will be posted below or [here](https://uqtools.larc.nasa.gov/the-nasa-and-dnv-challenge-on-optimization-under-uncertainty/).
