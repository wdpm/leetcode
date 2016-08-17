# 155. Min Stack
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

- push(x) -- Push element x onto stack.
- pop() -- Removes the element on top of the stack.
- top() -- Get the top element.
- getMin() -- Retrieve the minimum element in the stack.

**Example**:
```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```
## Solution1
``` java
public class MinStack {

    Stack<Integer> s=new Stack<>();
    Stack<Integer> minS=new Stack<>(); 
    /** initialize your data structure here. */
    public MinStack() {
        
    }
    
    public void push(int x) {
        s.push(x);
        if(!minS.isEmpty()&&x>minS.peek()){
            //dosen't need to update minS
            return;
        }
        minS.push(x);
    }
    
    public void pop() {
        int tmp=s.pop();
        if(tmp==minS.peek()){
            minS.pop();
        }
    }
    
    public int top() {
        return s.peek();
    }
    
    public int getMin() {
        return minS.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
 ```