# ABAP-DATABASE-TABLE-CEREATION-AND-CREATE-UPDATE-DELECT-BUSINESS-LOGIC-
DATABASE CREATION AND CUD OF BUSINESS LOGICS

![image](https://github.com/user-attachments/assets/8e3d53b6-11c3-4ba2-8419-ed5e658396e6)
![image](https://github.com/user-attachments/assets/c61cda55-dbbb-4e52-a919-10d26a318d6c)

before ----> ![image](https://github.com/user-attachments/assets/2ebddede-118b-41e4-b8a2-83a14f72afa6)

after -----> ![image](https://github.com/user-attachments/assets/02fd8d8f-5f6f-48a5-8edd-4f09c4a9e4a8)


REPORT ZTRIAL1.

tables : ZPURCHASE_INFO.

data : lv_found type ZPURCHASE_INFO.  


parameters :  p_1 type zpurchase_order.  
parameters : p_u TYPE abap_bool AS CHECKBOX USER-COMMAND act,               
parameters : p_d TYPE abap_bool AS CHECKBOX.  


START-OF-SELECTION.  

select single * from ZPURCHASE_INFO into @data(pur) where purchase_order = @p_1.

if sy-subrc = 0.
lv_found = 'X'.

if = 'X'.     
pur-AMOUNT = PUR-AMOUNT + 1000.     
modify  ZPURCHASE_INFO from @pur.    
endcase.
endif.


if p_d = abap_true.    
DELETE FROM zpurchase_info WHERE purchase_order = @p_1.  
endif.


else.  


case p_1.    
pur-purchase_order = p_1.   
pur-amount = 0.    
INSERT zpurchase_info FROM @pur.  
endcase.    
endif.




