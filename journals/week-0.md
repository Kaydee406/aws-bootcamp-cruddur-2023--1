# Week 0 Billing Architecture

## Required Homework

### Lucid chart conceptual Diagram

The diagram below shows a conceptual diagram for the illustration of our app design in **Lucid Charts**

![](assets/lucid%20chart%20diagramassgnment.PNG)

[Lucid Chart Share link](https://lucid.app/lucidchart/75d122cd-ba32-4331-889f-d1dc880b85a4/edit?viewport_loc=-776%2C-106%2C3002%2C1372%2C0_0&invitationId=inv_d32d896e-c800-424a-a8cb-99a132d510e1)

### Create a Billing Alarm
[Aws Billing alarm link]({
    "AlarmName": "DailyEstimatedCharges",
    "AlarmDescription": "This alarm would be triggered if the daily estimated charges exceeds 1$",
    "ActionsEnabled": true,
    "AlarmActions": [
        "arn:aws:sns:ca-central-1:700579005047:billing-alarm"
    ],
    "EvaluationPeriods": 1,
    "DatapointsToAlarm": 1,
    "Threshold": 1,
    "ComparisonOperator": "GreaterThanOrEqualToThreshold",
    "TreatMissingData": "breaching",
    "Metrics": [{
        "Id": "m1",
        "MetricStat": {
            "Metric": {
                "Namespace": "AWS/Billing",
                "MetricName": "EstimatedCharges",
                "Dimensions": [{
                    "Name": "Currency",
                    "Value": "USD"
                }]
            },
            "Period": 86400,
            "Stat": "Maximum"
        },
        "ReturnData": false
    },
    {
        "Id": "e1",
        "Expression": "IF(RATE(m1)>0,RATE(m1)*86400,0)",
        "Label": "DailyEstimatedCharges",
        "ReturnData": true
    }]
  })
  
### Create a Budget
The diagram below is a snapshot of my aws budget alarm created on my *aws console*

![](assets/aws%20budget%20assignment.PNG)
