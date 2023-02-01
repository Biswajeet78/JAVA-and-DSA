class Solution {
    public String gcdOfStrings(String s1, String s2) {
        if(!(s1+s2).equals(s2+s1))
        {
            return "";
        }
        else if(s1.equals(s2))
        {
            return s1;
        }
        else if( s1.length() > s2.length())
        {
            return gcdOfStrings(s1.substring(s2.length()), s2);
        }
        else
        {
            return gcdOfStrings(s2.substring(s1.length()) , s1);
        }
    }
}
