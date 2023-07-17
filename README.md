# Procure-to-Pay Analysis: A Proces Mining Approach

This repository contains a data analytics project that utilizes process mining methodology to analyse and improve the procure-to-pay process of a company.

# Project Overview
The goal of this project is to:
1. Utilize process mining techniques to uncover the complete procurement process
2. Identify inefficiencies and potential process bottlenecks.
3. Generate insights to improve process efficiency.

# Methodology
1. Data Collection:
2. Data Preparation:
3. Process Discovery:
4. Performance Analysis:
5. Process Improvement:

# Technologies Used
1. Python
2. Pandas
3. Graphviz library
4. Jupyter Notebook
5. Matplotlib library
6. Microsoft PowerBI

# Data collection
![alt text]
The event log consists of 1696 cases between January 2015 and August 2017. Although, majority of the cases happened in 2017. Each procurement contains the following attributes
- <b>Document date</b>: 
- <b>Invoice received</b>: The date the invoice is received from the Vendor
- <b>1st approval</b>: The date the invoice was first approved
- <b>2nd approval</b>: The date the invoice was approved by the 2nd approver
- <b>Posting date</b>: When the invoice was posted to the system
- <b>Payment performed</b>: When the payment was made to the Vendor
- <b>Entity</b>: all cases relates to one entity - 4097 
- <b>Account</b>: The unique identifier of the Vendor. We will be using this rather than the Vendor Name
- <b>Comment</b>: If the process was a reversal of an existing process
- <b>Gross Amount</b>: The gross amount for each case

# Data preparation
The event log data was cleaned and transformed into a suitable format for process mining. This includes the following:
The following activities were carried out:
- Rename the columns to make them easier to reference and understand
- Melt the data to get the dataframe into the required format for process mining
- Remove rows with missing times. This is because from the dataset received, those activities do not occur in that particular purchase order.
- Sort the event log using the unique identifier (<b>Document No.</b>) and Date column. This is to arrange each Purchase document accoring to how the activities were performed (by date)
- Extracted completed cases. I assumed that the process is complete when the payment has been made (i.e., the last activity is <b>Payment performed</b>).
- PowerBI Data format. One of the weakness I have noticed when using PowerBI for process mining is that where two activities are performed on the same date, it sorts these activities alphabetically. For example, if the <b>posting date</b> and <b>payment performed</b> activities were performed on the same day, the payment performed activity would come first before posting date even though in jupyter notebook, posting date comes first. To avoid this, I  included an <b>Event_ID</b> column so that to sort the activities properly in Powerbi.

# Process discovery
![alt text]
The Graphviz library was used to automatically generate a visual process model based on the event log data. 
1. <b>Variant analysis</b>: This variant analysis shows how frequently a particular process is followed. From the above, we can see that there is a total of 26 variants. The first 4 variants account for about 83% of all process, Meanwhile 7 variants occur only once. There are some cases which were completed without any approval. These cases have been captured in Variants 1, 3, 9 and 16 comprise 694 cases.
2. <b>Process graph</b>: The process graph shows how the activity flows from the start of a procurement process to the end. From the process graph, not all the cases need both approval. There are more of 1st approvals than 2nd approvals. In addition, there are four different start cases i.e., <i>Document Date</i>, <i>Invoice Received</i>, <i>1st approval</i>, and <i>Posting Date</i>. 694 payments representing 47% of the cases were made without approval. Out of these payments, 17 were reversals.
3. <b>Transition matrix</b>: The transition matrix shows how the events are been handed over from one to another and how frequently this occurs. From the above, it can be seen that <i>Payment performed</i> activity is not followed by any other activity i.e., that is the end of the process. However, all other events can be done before <i>Payment Performed</i> in no particular order. The most frequently occuring activity before <i>Payment performed</i> is the <i>Posting Date</i>. <i>Document Date</i> is mostly followed by <i>Invoice Received</i> and <i>Invoice Received</i> is mostly followed by <i>1st approval</i>. <i>2nd approval</i> is majorly done after <i>1st approval</i>. One thing to note from the transition matrix is that all other event can happen after <i>Posting Date</i>. It begs the question when should a procurement be posted? After approval?
4. <b>Other findings</b>: From the above, it can be seen that there are some events which happen on Saturday and Sunday. 6 payments were made on Saturday and 1 on Sunday. The most frequently occuring activity in the weekend was <i>Document Date</i> which occured 156 times

# Performance analysis


# Vendor dashboard


# Process improvement

# Limitation
No information about users
