1)  Configure ADLS to ADF to ADB (Mounting)
![[Pasted image 20240426161809.png]]
2)  We have read the data by 
![[Pasted image 20240426161957.png]]
3) And saw the day by show and also with printSchema we have checked the type of the data, 
		to change the type manually, we have written below code
		![[Pasted image 20240426162144.png]]
4) The effort can be reduced if we use option("InferSchema","true") 	
5) Some basic transformations
![[Pasted image 20240426165901.png]]
![[Pasted image 20240426165916.png]]
6) Writing files to transformed data container
![[Pasted image 20240426165946.png]]
