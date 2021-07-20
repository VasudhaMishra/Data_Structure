# Data_Structure
Include all important DS question topic-wise

Tree traversal

1. **Pre-Order Traversal**

  
    
       class Solution {
    
       public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        if(root == null) return list;
        
        Stack<TreeNode> stack = new Stack<>();
        stack.push(root);
        
        while(!stack.isEmpty()){
            
            TreeNode current = stack.pop();
            list.add(current.val);
            
            if(current.right!=null) stack.push(current.right);
            if(current.left!=null) stack.push(current.left);
        }
        return list;
       }
       }
  
  
  2. **In Order Traversal**
  

         class Solution {
     
         public List<Integer> inorderTraversal(TreeNode root) {
  
         List<Integer> res = new LinkedList<Integer>();
	       if (root == null) return res;
	
	       Stack<TreeNode> stack = new Stack<TreeNode>();
	       TreeNode cur = root;
	       while (cur != null || !stack.isEmpty()) { 
  
		       while (cur != null) {
             // Travel to each node's left child, till reach the left leaf
			       stack.push(cur);
			       cur = cur.left;				
		        }		 
		      cur = stack.pop(); // Backtrack to higher level node A
		      res.add(cur.val);  // Add the node to the result list
		      cur = cur.right;   // Switch to A'right branch
	       }
	       return res;
         }
         }
  
  **3. Post Order Traversal**
  
       class Solution {
          public List<Integer> postorderTraversal(TreeNode root) {
          List<Integer> res = new ArrayList<Integer>();
          if(root==null) return res;
        
          Stack<TreeNode> stack = new Stack<TreeNode>();
          stack.push(root);
        
          while(!stack.isEmpty()){
                TreeNode curr = stack.pop();
                res.add(0,curr.val);
                
                if(curr.left!=null){
                    stack.push(curr.left);
                }
                if(curr.right!=null){
                    stack.push(curr.right);
                }
            }
          return res;
         }
        }
  
  
  **4. Level Order traversal**
  
       class Solution {
         public List<List<Integer>> levelOrder(TreeNode root) {
        
         List<List<Integer>> mainList = new ArrayList<List<Integer>>();
         if(root == null) return mainList;
        
          List<Integer> levelList = new ArrayList<Integer>();
        
          Queue<TreeNode> queueList = new LinkedList<TreeNode>();
          queueList.offer(root);
          queueList.offer(null);
        
          while(!queueList.isEmpty()){
            TreeNode node = queueList.poll();
            if(node!=null){
                levelList.add(node.val);
            }
            else{
                mainList.add(levelList);
                if(queueList.isEmpty()){
                    break;
                }
                levelList = new ArrayList<Integer>();
                queueList.offer(null);
                continue;
            }
            
            if(node.left!=null){
                queueList.offer(node.left);
            }
            if(node.right!=null){
                queueList.offer(node.right);
            }
            
          }
          return mainList;
         }
       }
