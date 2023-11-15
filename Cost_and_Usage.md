# Cost and Usage


## Programatically


```
case `uname -o` in
  Darwin) START_DATE=$(date -v-14d +"%Y-%m-%d") ;;
  'GNU/Linux') START_DATE=$(date -d "$date -14 days" +"%Y-%m-%d") ;;
esac
END_DATE=$(date +%F)
echo "Start Date: $START_DATE"
echo "End Date: $END_DATE"

aws ce get-cost-and-usage-with-resources  \
  --granularity MONTHLY \
  --time-period Start=$START_DATE,End=$END_DATE \
  --filter '{"Dimensions": { "Key": "INSTANCE_TYPE", "Values": [ "UsageQuantity", "BlendedCosts", "RESOURCE_ID" ] }}' \
  --metrics "BlendedCost" "UsageQuantity" \
  --group-by Type=DIMENSION,Key=INSTANCE_TYPE Type=DIMENSION,Key=RESOURCE_ID 
```


## ProTip(s)
> An error occurred (ValidationException) when calling the GetCostAndUsageWithResources operation: start date is too old for hourly, the max supported days for hourly granularity is 14 days
[API Documentation](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetCostAndUsageWithResources.html#API_GetCostAndUsageWithResources_RequestSyntax)  explains this. 

## References
https://calculator.aws/#/  
https://docs.aws.amazon.com/cli/latest/reference/ce/get-cost-and-usage.html  
https://docs.aws.amazon.com/cli/latest/reference/ce/get-cost-and-usage-with-resources.html  


