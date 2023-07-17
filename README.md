Procure-to-Pay Analysis: A Proces Mining Approach

This repository aims to apply process mining approach to a procure-to-pay process. The process contains the following (adjusted) activities: 
- <b>Document date</b>: 
- <b>Invoice received</b>: The date the invoice is received from the Vendor
- <b>1st approval</b>: The date the invoice was first approved
- <b>2nd approval</b>: The date the invoice was approved by the 2nd approver
- <b>Posting date</b>: When the invoice was posted to the system
- <b>Payment performed</b>: When the payment was made to the Vendor

Other information contained in the event log includes the following
* <b>Entity</b>: all cases relates to one entity - 4097 
* <b>Account</b>: The unique identifier of the Vendor. We will be using this rather than the Vendor Name
* <b>Comment</b>: If the process was a reversal of an existing process
* <b>Gross Amount</b>: The gross amount for each case

The event log consists of 1696 cases between January 2015 and August 2017. Although, majority of the cases happened in 2017.
