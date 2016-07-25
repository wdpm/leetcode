# 242. Valid Anagram
Given two strings s and t, write a function to determine if t is an anagram of s.

For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

Note:
You may assume the string contains only lowercase alphabets.

## Solution1
``` js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    //参考来源:https://discuss.leetcode.com/topic/51684/based-on-jave-simple-and-efficient-solution
    //思路：使用哈希表来存放，键为字符，值为出现的次数
    //遍历时，相应地减少特定字符的出现次数，如果值出现负值，那么必然不是Anagram
    if(s.length===0 &&t.length===0){
        return true;
    }
    
    if(s.length!==t.length){
        return false;
    }
    
    //初始化计数器
    var count=new Array(26);
    for(var k=0;k<26;k++){
        count[k]=0;
    }
    // console.log(count);
    //记录s
    for(var i=0;i<s.length;i++){
        count[s.charCodeAt(i)-'a'.charCodeAt(0)]++;
    }
    
    //遍历t
    for(var j=0;j<t.length;j++){
        var cht=t.charCodeAt(j);
        count[cht-'a'.charCodeAt(0)]--;
        //相应字符在t中的出现次数如果小于0
        if(count[cht-'a'.charCodeAt(0)]<0){
            return false;
        }
    }
    
    return true;
};
```

## Solution2
``` java
public class Solution {
    public boolean isAnagram(String s, String t) {
        //参考来源:https://discuss.leetcode.com/topic/47436/my-java-solution-about-valid-anagram-very-easy-8ms
        //长度都为0
        if(s.length()==0 && t.length()==0){
            return true;
        }
        
        //长度不等
        if(s.length()!=t.length()){
            return false;
        }
        
        char[] chs=s.toCharArray();
        char[] cht=t.toCharArray();
        
        Arrays.sort(chs);
        Arrays.sort(cht);
        
        //长度相等,遍历比较相同位置的元素
        for(int i=0;i<chs.length;i++){
            if(chs[i]!=cht[i]){
                return false;
            }
        }
        
        return true;
    }
}
```

## Solution3
``` java
//效率很低，但能AC
public class Solution {
    public boolean isAnagram(String s, String t) {
        
        if(s.length()==0&&t.length()==0){
            return true;
        }
        
        if(s.length()!=t.length()){
            return false;
        }
        
        //存放s
        List list1=new ArrayList<>();
        //存放t
        List list2=new ArrayList<>();
        
        for(int i=0;i<s.length();i++){
            list1.add(s.charAt(i));
        }
        
        for(int j=0;j<t.length();j++){
            list2.add(t.charAt(j));
        }
        
        //遍历
        for(int k=0;k<list1.size();k++){
            //list2中含有list1中某元素，则从list2中删除该元素
            if(list2.contains(list1.get(k))){
                list2.remove(list2.indexOf(list1.get(k)));
            }else{
               return false;
            }

        }            
        return true;
    }
}
```