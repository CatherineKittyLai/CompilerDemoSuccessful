# CompilerDemoSuccessful
Final project 
#################環境###################### 

windows，下載Bison、flex、MinGW

#################作法###################### 
#lex的部分就仿照之前的compiler上課ppt做出

#Yacc部分: 
#1.先把Grammar全部打好 
#2.處理variable的部分,在此我使用stack來做

# 在第11行定義node格式 
 #typedef struct node{//node格式 
 #---------略------------ 
 #};

 #第52行，我們得知道現在在stack的變數有哪些 
 #struct node *search_in_stack(struct node *start){//search現在有哪些變數在stack中 
 #--------略--------- 
 #};

 #第211行，找到變數後，若是新變數就放進stack，若不是就修改值 
 #void put_in_stack(struct node *now){//找到函數後，若是新函數就放進stack，若不是則修改 
 #-----------略------------------- 
 #}

#3.number op 與 logic op 的處理 
 #第76行先做num op struct 
 #node *evl_num_op(int op_type, struct node *a, struct node b){//num op calculate 
 #------略-------- 
 #if(op_type==1){//+ 
 #------略-------- 
 #else if(op_type==2){//- 
 #------略-------- } 
 #else if(op_type==3){// *
 #------略-------- } 
 #else if(op_type==4){// / 
 #------略-------- } 
 #else if(op_type==5){//mod 
 #------略-------- } 
 #else if(op_type==6){//> 
 #------略-------- } 
 #else if(op_type==7){//<
 #------略-------- } 
 #else if(op_type==8){//= 
 #------略-------- } 
 #return tem; 
 #};

 #第170行做logic op compare 
 #struct node *evl_logic_op(int op_type, struct node *a, struct node *b){//logic op compare 
 #------略-------- 
 #if(op_type==1){//and 
 #------略-------- } 
 #else if(op_type==2){//or 
 #------略-------- } 
 #else if(op_type==3){//not 
 #------略-------- } 
 #return tem; 
 #}

#4.輸出值 
#第235行，當為2number、3variable、4num-op、8if-exp直接輸出值；若為1bool、5logic-op、9define-var則依判斷輸出#t或#f；若以上皆非則輸出syntax error 
void print_stmt(struct node *now, int n_or_b){//輸出值
if(n_or_b==2||n_or_b==3||n_or_b==4||n_or_b==8){
	printf("%d\n",now->value);
}
else if(n_or_b==1||n_or_b==5||n_or_b==9){
	if(now->value==1){
		printf("#t\n");
	}
	else{
		printf("#f\n");
	}
}
else{
	printf("syntax error\n");
	exit(0);
}
}

##########結語########### 
#沒做出function的部分
