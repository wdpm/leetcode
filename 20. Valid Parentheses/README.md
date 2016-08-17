# 20. Valid Parentheses
Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.

## Solution1
``` js
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    //helper: check match
    function match(open,close){
        var opens='([{';
        var closes=')]}';
        return opens.indexOf(open)===closes.indexOf(close);
    }
    
    //helper: simulate stack
    function Stack(){
        var items=[];
        
        this.push=function(x){
            items.push(x);
        }
        
        this.pop=function(){
            return items.pop();
        }
        
        this.isEmpty=function(){
            return items.length===0;
        }
    }

    var len=s.length;
    var index=0;
    var valid=true;
    var stack=new Stack();
    var pop,
        char;
    while(index<len && valid){
        char=s[index];
        //opens char
        if(char==='('||char==='['||char==='{'){
            stack.push(char);
        }else{//closes char
            //no char in stack to match this char
            if(stack.isEmpty()){
                valid=false;
            }else{
                pop=stack.pop();
                if(!match(pop,char)){
                    valid=false;
                }
            }
        }
        index++;
    }
    
    return !!(valid && stack.isEmpty());
};
``