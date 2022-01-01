##                   Kappa : 0.9943          

##  Mcnemar's Test P-Value : NA              

## 

## Statistics by Class:

## 

##                      Class: A Class: B Class: C Class: D Class: E

## Sensitivity            0.9993   0.9968   0.9895   0.9900   0.9989

## Specificity            0.9994   0.9977   0.9983   0.9995   0.9995

## Pos Pred Value         0.9986   0.9906   0.9918   0.9975   0.9978

## Neg Pred Value         0.9997   0.9992   0.9978   0.9981   0.9998

## Prevalence             0.2845   0.1935   0.1743   0.1639   0.1837

## Detection Rate         0.2843   0.1929   0.1725   0.1623   0.1835

## Detection Prevalence   0.2847   0.1947   0.1739   0.1627   0.1839

## Balanced Accuracy      0.9994   0.9973   0.9939   0.9948   0.9992

```



## Conclusion



### Result



The confusion matrices show, that the Random Forest algorithm performens better than decision trees. The accuracy for the Random Forest model was 0.995 (95% CI: (0.993, 0.997)) compared to 0.739 (95% CI: (0.727, 0.752)) for Decision Tree model. The random Forest model is choosen.



### Expected out-of-sample error

The expected out-of-sample error is estimated at 0.005, or 0.5%. The expected out-of-sample error is calculated as 1 - accuracy for predictions made against the cross-validation set. Our Test data set comprises 20 cases. With an accuracy above 99% on our cross-validation data, we can expect that very few, or none, of the test samples will be missclassified.



## Submission

In this section the files for the project submission are generated using the random forest algorithm on the testing data.





```r

# Perform prediction

predictSubmission <- predict(modFitRF, testing, type="class")

predictSubmission

```



```

##  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 

##  B  A  B  A  A  E  D  B  A  A  B  C  B  A  E  E  A  B  B  B 

## Levels: A B C D E

```



```r

# Write files for submission

pml_write_files = function(x){

  n = length(x)

  for(i in 1:n){

    filename = paste0("./data/submission/problem_id_",i,".txt")

    write.table(x[i],file=filename,quote=FALSE,row.names=FALSE,col.names=FALSE)

  }

}



pml_write_files(predictSubmission)

```
