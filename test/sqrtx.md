# sqrtx
>  [http://www.lintcode.com/en/problem/sqrtx](http://www.lintcode.com/en/problem/sqrtx)

二分法要注意写法


错误写法会造成溢出

	class Solution {
	public:
	    /**
	     * @param x: An integer
	     * @return: The sqrt of x
	     */
	    int sqrt(int x) {
	        // write your code here
	        if (x == 0) return 0;
	        int start = 0;
	        int end = x;
	        int mid = start + (end - start)/2;
	        long long tmp;
	        while (end - start > 1) {
	            mid = start + (end - start)/2;
	            tmp = mid * mid;
	            if (tmp > x) {
	                end = mid;
	            } else if (tmp < x) {
	                start = mid;
	            } else {
	                return mid;
	            }
	        }
	        if (start * start > x) {
	            return start - 1;
	        } else if (x >= start * start && x < end * end) {
	            return start;
	        } else if (x >= end * end) {
	            return end;
	        }
	    }
	};

正确写法，但是要注意，不要被0除

	class Solution {
	public:
	    /**
	     * @param x: An integer
	     * @return: The sqrt of x
	     */
	    int sqrt(int x) {
	        // write your code here
	        if (x == 0) return 0;
	        if (x == 1) return 1;
	        int start = 0;
	        int end = x;
	        int mid = start + (end - start)/2;
	        while (end - start > 1) {
	            mid = start + (end - start)/2;

	            if (mid > x/mid) {
	                end = mid;
	            } else if (mid < x/mid) {
	                start = mid;
	            } else {
	                return mid;
	            }
	        }
	        if (start > x/start) {
	            return start - 1;
	        } else if (x/start >= start && x/end < end) {
	            return start;
	        } else {
	            return end;
	        }
	    }
	};

另外可以使用牛顿迭代法
