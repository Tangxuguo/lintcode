# subsets

先排序

然后 DFS & 回溯法

递归如下逻辑：

	Func subsetHelper
	对于输入字符串s及子集合
        选取子集合输出
        循环如果当前字符不是最后一位字符
        		 添加该字符
                 递归调用subsetHelper,处理下一位字符
                 删除上面添加的字符，即集合中没有该字符

流程图：
<img src="/blog/public/images/posts/code/subsets.png" >

输出顺序{}，{1}，{1，2}，{1,2,3}, {1,2,3,4}, {1,2,4}, {1，3}，{1,3,4}, {1，4}，{2}，{2，3}，{2,3,4}, {2，4}，{3}，{3，4}，{4}

代码

	class Solution {
	public:
	    /**
	     * @param S: A set of numbers.
	     * @return: A list of lists. All valid subsets.
	     */
	    vector<vector<int> > subsets(vector<int> &S) {
	    	// write your code here
	    	vector<vector<int>> result;
	        vector<int> path;
	        sort(S.begin(),S.end());
	        subsetsHelper(result,path,0,S);
	        return result;
	    }

	    void subsetsHelper(vector<vector<int> > &result, vector<int> &path,int pos, vector<int> &S){
	        result.push_back(path);
	        for(int i=pos; i< S.size(); i++){
	            path.push_back(S[i]);
	            subsetsHelper(result, path, i+1, S);
	            path.pop_back();
	        }
	    }

};
