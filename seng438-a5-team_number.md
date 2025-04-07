**SENG 438- Software Testing, Reliability, and Quality**

**Lab. Report \#5 – Software Reliability Assessment**

| Group 22:       |   |
|-----------------|---|
| Student Names:  | Issy Gaudet         |
|                 | Kamand Ghorbanzadeh |
|                 | Spiro Douvis        |
|                 | Dylan Wenaas        |

# Introduction

The main purpose of this lab was to help us discover the reliability assessment and the usage of the tools such as C-SFRAT and the Reliability Demonstration Chart with the help of Excel. This lab assignment also explored the failure reliability growth testing which helps analyze the product’s changes over a period of time. Additionally, this lab also introduced to us the concept of failure data which is critical to analyze as it can aid us in determining how to prevent future failures. Overall, these new concepts solidified the theoretical lectures helped us understand where reliability testing plays its role in software testing procedures.

# 

# Assessment Using Reliability Growth Testing 

# Assessment Using Reliability Demonstration Chart 

## 3 plots for MTTFmin, twice and half of it for your test data

### RDC for MTTFmin
![alt text](image.png)

### RDC for twice MTTFmin
![alt text](image-2.png)

### RDC for half MTTFmin
![alt text](image-1.png)

## Explain your evaluation and justification of how you decide the MTTFmin

To determine the MTTFmin, we used the RDC-11 Excel tool, which plots the system’s failure behavior on a reliability demonstration chart. Our goal was to identify the lowest possible MTTF where the failure points still fall within the acceptable and continue-test regions, based on a specified maximum number of allowable failures.

We began by selecting Failure Report 3, which includes 24 failure times. Since RDC-11 only accepts 16 failure entries, we used the first 16 failures.

To evaluate and determine the minimum acceptable MTTF, we started by using the standard MTTF formula:

MTTF = Total Operating Time / Number of Failures
​
From the failure data, we used 16 failure observations out of the original 24, with the 16th failure occurring at 614 seconds. Using this, we estimated the observed MTTF as:

MTTF = 614 / 16 ≈ 38.4 seconds

Since this value was close to 40, we decided to test whether 40 seconds could be used as a reasonable MTTFmin and used that value as a rough baseline for our trial and error.

To do this in the RDC-11 tool, we worked backward. The tool doesn’t let us input MTTFmin directly, so we used trial and error by adjusting the "Number of Input Events" value in the RDC settings to achieve a normalized usage unit (X-axis) near 40.

We set 'Maximum acceptable number of failures' to 5 and 'Input event description' to seconds (representing system runtime).

We chose 5 failures because this is a reasonable threshold to reflect a system’s performance while still keeping the number of failures manageable for assessing reliability. A lower number of failures allows for a more precise evaluation of the system’s reliability, while higher failure numbers might stretch the system beyond acceptable performance limits. We felt 5 was a fair number of failures to estimate with.

We then adjusted the "Number of Input Events" until we found a setup that provided a good fit for the system's failure behavior. Next, we continued refining our estimate of MTTFmin by further adjusting the "Number of Input Events" value. As we ran multiple trials, we observed how the failure points shifted relative to the acceptable region on the chart. When we set the MTTFmin to 46 seconds, the majority of the failure points fell within the acceptable boundary. However, at smaller values, such as 40 seconds, more failure points fell outside the acceptable region, indicating that the system wouldn't meet the required reliability performance. After several iterations, we found that adjusting the 'Number of Input Events' to 230 yielded the best results. This setup resulted in an estimated MTTFmin of:

Estimated MTTFmin = 230 input events / 5 failures = 46 seconds

Thus, after evaluating multiple trials and observing the trend in the RDC chart, we concluded that an MTTFmin of 46 seconds was the minimum value at which the system demonstrated acceptable reliability, based on our failure data and assumptions in the RDC-11 tool.

## A discussion on the advantages and disadvantages of RDC	

Advantages:

RDC is very versatile, it can be applied to a wide range of systems to evaluate their reliability. It is useful in various industries and for different types of products, making it an adaptable tool. RDC is also very time efficient, its able to conduct reliability analysis in a relatively short period. It is also cost-effective since it doesn't require complex equipment or a large team of experts to implement, especially when using the open-source Excel version of RDC like we used for this assignment. The RDC also allows for experimentation with different values for confidence levels and MTTF. This feature is useful for conducting "what-if" scenarios, where you can analyze how changes in these variables affect the system's reliability. This flexibility helps in decision-making and optimization processes. While RDC cannot provide exact quantitative reliability values, it gives a straightforward way to assess whether a SUT is acceptable or not based on predefined criteria, making it easier to make quick judgments on system performance.

Disadvantages:

A significant drawback of the RDC is that it cannot calculate the precise quantitative reliability or availability of the system being studied. This limits its ability to provide in-depth insights into system performance and long-term reliability. Since RDC only indicates whether the system is acceptable or not based on the predefined confidence levels and MTTF values, it doesn’t provide a full spectrum of reliability metrics. This can be limiting in situations where detailed, quantitative reliability data is required for in-depth analysis.

In conclusion, while RDC offers a versatile, efficient, and cost-effective way to perform reliability assessments, it does come with limitations related to the precision of the results it provides. It is good for quick assessments and scenarios where a simple pass/fail decision is what we want. 

# Comparison of Results

# Discussion on Similarity and Differences of the Two Techniques

Both reliability growth testing and reliability assessment using RDC are techniques used to evaluate the reliability of a SUT, and although they share some similarities, they differ significantly in their methodologies and applications.

Similarities
- Both techniques use failure times and more specifically MTTF to assess the system’s performance and reliability.
- Failure data is needed for both methods. The same dataset was used as input for both techniques in our testing process.
- Both methods used to determine whether the system is becoming more reliable over time, either through improved failure trends or a longer MTTF.
- Both methods requires tools and analysis techniques. Reliability growth testing uses statistical modeling and trend analysis, RDC uses graphical interpretation through tools like RDC-11.

Differences
- The data collection approach is different. In reliability growth testing, failures are continuously monitored and recorded as they occur but for RDC failure data is collected at predefined intervals.
- The analysis method. Reliability growth testing focuses on viewing trends and patterns in failure rates using statistical models, RDC involves plotting cumulative failures against normalized input events to determine if the system falls in the Accept, Reject, or Continue Testing regions.
- In reliability growth testing, both failure counts and inter-failure times are considered to analyze trends over time but RDC focuses on inter-failure times to assess reliability at specific checkpoints.
- Reliability growth testing is more data-intensive and often part of a continuous improvement process, it helps identify and address reliability issues as they appear, RDC is simpler and provides just a pass/fail type decision based on limited failure data.
- Growth testing focuses on predicting reliability trends, and RDC focuses on determining whether the system meets a specific reliability requirement at a point in time.

# How the team work/effort was divided and managed

**Kamand and Spiro:** Kamand and Spiro collaborated on Part 1 of the lab, which focused on reliability growth testing using the C-SFRAT tool. We worked together to analyze the failure data, create the required plots for MTTFmin, twice MTTFmin, and half MTTFmin, and evaluate the failure rate and reliability of the SUT. We also contributed to the discussion on the advantages and disadvantages of reliability growth testing and documented the decision-making process for selecting the appropriate models.

**Isabelle and Dylan:** Isabelle and Dylan worked on Part 2 of the lab, which involved using the Reliability Demonstration Chart (RDC) tool. We determined the MTTFmin through trial and error by adjusting the "Number of Input Events" and setting parameters such as the "Maximum Acceptable Number of Failures." We also created the required plots for MTTFmin, twice MTTFmin, and half MTTFmin, and analyzed the results. Additionally, we contributed to the discussion on the advantages and disadvantages of RDC and documented the challenges encountered during the process.

**Team Collaboration:** The entire team collectively worked on the write-up for the lab report. This included comparing the results of Part 1 and Part 2, discussing the similarities and differences between the two techniques, and reflecting on the lessons learned during the lab. Regular meetings and discussions ensured that all sections were cohesive and well-structured. Each member reviewed the final document to ensure consistency, accuracy, and clarity.

# Difficulties encountered, challenges overcome, and lessons learned

Determining the MTTFmin using the RDC-11 tool had several challenges. The tool doesn’t allow for direct input of MTTFmin, so we had to use trial and error by adjusting the "Number of Input Events" to achieve a normalized usage unit close to our target. One difficulty was selecting the right parameters, such as setting the "Maximum Acceptable Number of Failures" to 5, which we felt was a reasonable value for evaluating reliability without pushing the system’s limits. Refining the MTTFmin estimate was challenging as it required multiple iterations to find the optimal value, with 230 input events producing a normalized usage unit of approximately 46 seconds. It was also hard to determine the best estimate/when to stop since the RDC-11 tool only provides a graph with color coded regions and gives no specific values indicating how accurate or reliable the result was, making it difficult to know how good our estimates were compared to eachother.

# Comments/feedback on the lab itself
