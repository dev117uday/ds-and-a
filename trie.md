# Trie

## Representation, Search and Insert

```java
public class Trie { 
	

	static final int ALPHABET_SIZE = 26; 
	
	
	static class TrieNode 
	{ 
		TrieNode[] children = new TrieNode[ALPHABET_SIZE]; 
	
	
		boolean isEndOfWord; 
		
		TrieNode(){ 
			isEndOfWord = false; 
			for (int i = 0; i < ALPHABET_SIZE; i++) 
				children[i] = null; 
		} 
	}; 
	
	static TrieNode root; 
	

	static void insert(String key) 
	{ 
		int level; 
		int length = key.length(); 
		int index; 
	
		TrieNode pCrawl = root; 
	
		for (level = 0; level < length; level++) 
		{ 
			index = key.charAt(level) - 'a'; 
			if (pCrawl.children[index] == null) 
				pCrawl.children[index] = new TrieNode(); 
	
			pCrawl = pCrawl.children[index]; 
		} 
	
		 
		pCrawl.isEndOfWord = true; 
	} 
	
	
	static boolean search(String key) 
	{ 
		int level; 
		int length = key.length(); 
		int index; 
		TrieNode pCrawl = root; 
	
		for (level = 0; level < length; level++) 
		{ 
			index = key.charAt(level) - 'a'; 
	
			if (pCrawl.children[index] == null) 
				return false; 
	
			pCrawl = pCrawl.children[index]; 
		} 
	
		return (pCrawl != null && pCrawl.isEndOfWord); 
	} 
	
	 
	public static void main(String args[]) 
	{ 
		
		String keys[] = {"bad", "bat", "geeks", "geeks", "cat", 
						"cut"}; 
	
		String output[] = {"NO", "YES"}; 
	
	
		root = new TrieNode(); 
	
		
		int i; 
		for (i = 0; i < keys.length ; i++) 
			insert(keys[i]); 
	
		
		if(search("bad") == true) 
			System.out.println("bad --- " + output[1]); 
		else System.out.println("bad --- " + output[0]); 
		
		if(search("geeks") == true) 
			System.out.println("geeks --- " + output[1]); 
		else System.out.println("geeks --- " + output[0]); 

		if(search("ca") == true) 
			System.out.println("ca --- " + output[1]); 
		else System.out.println("ca --- " + output[0]); 
		
		
	} 
}

```

## Trie Delete

```java
public class Trie { 
	

	static final int ALPHABET_SIZE = 26; 
	
	
	static class TrieNode 
	{ 
		TrieNode[] children = new TrieNode[ALPHABET_SIZE]; 
	
	
		boolean isEndOfWord; 
		
		TrieNode(){ 
			isEndOfWord = false; 
			for (int i = 0; i < ALPHABET_SIZE; i++) 
				children[i] = null; 
		} 
	}; 
	
	static TrieNode root; 
	

	static void insert(String key) 
	{ 
		int level; 
		int length = key.length(); 
		int index; 
	
		TrieNode pCrawl = root; 
	
		for (level = 0; level < length; level++) 
		{ 
			index = key.charAt(level) - 'a'; 
			if (pCrawl.children[index] == null) 
				pCrawl.children[index] = new TrieNode(); 
	
			pCrawl = pCrawl.children[index]; 
		} 
	
		 
		pCrawl.isEndOfWord = true; 
	} 
	
	
	static boolean search(String key) 
	{ 
		int level; 
		int length = key.length(); 
		int index; 
		TrieNode pCrawl = root; 
	
		for (level = 0; level < length; level++) 
		{ 
			index = key.charAt(level) - 'a'; 
	
			if (pCrawl.children[index] == null) 
				return false; 
	
			pCrawl = pCrawl.children[index]; 
		} 
	
		return (pCrawl != null && pCrawl.isEndOfWord); 
	} 
	
	 
	static TrieNode remove(TrieNode root,String key, int i) 
    { 
        
        
        if (root == null) 
            return null; 
      
        
        if (i == key.length()) { 
      
            
            if (root.isEndOfWord) 
                root.isEndOfWord = false; 
      
            
            if (isEmpty(root)) { 
               
                root = null; 
            } 
      
            return root;
        } 
      
        
        int index = key.charAt(i) - 'a'; 
        root.children[index] =  
        remove(root.children[index], key, i + 1); 
      
        
        if (isEmpty(root) && root.isEndOfWord == false) { 
            root = null; 
        } 
      
        return root; 
    } 
     
    static boolean isEmpty(TrieNode root) 
    { 
        for (int i = 0; i < ALPHABET_SIZE; i++) 
            if (root.children[i] != null) 
                return false; 
        return true; 
        
    } 
    
	public static void main(String args[]) 
	{ 
		
		String keys[] = {"an", "and", "ant", "bad", "bat", "zoo"}; 
	
		String output[] = {"NO", "YES"}; 
	
	
		root = new TrieNode(); 
	
		
		int i; 
		for (i = 0; i < keys.length ; i++) 
			insert(keys[i]); 
	
		
		root = remove(root, "zoo", 0);
		
		
		if(search("zoo") == true) 
			System.out.println("zoo --- " + output[1]); 
		else System.out.println("zoo --- " + output[0]); 
		
	
		
	} 
}
```

## **Count Distinct Rows in a Binary Matrix**

```java
public class Trie { 
	

	static final int M  = 4, N = 3; 
	static int mat[][] = {{1, 0, 0},  
                          {1, 1, 1},  
                          {1, 0, 0},  
                          {0, 1, 0}};
	
	static class TrieNode 
	{ 
		TrieNode[] child = new TrieNode[2]; 
    
	}; 
	
	static TrieNode root; 
	

	static boolean insert(TrieNode root, int row) 
	{ 
	    TrieNode curr = root;
	    boolean flag = false;
	    
	    for(int i = 0; i < N; i++)
	    {
	        int index = mat[row][i];
	        
	        if(curr.child[index] == null)
	        {
	            curr.child[index] = new TrieNode();
	            flag = true;
	        }
	        
	        curr = curr.child[index];
	    }
	    
	    return flag;
	} 
	
	

	 static int countDis()
	 {
	     TrieNode root = new TrieNode();
	     
	     int res = 0;
	     
	     for(int row = 0; row < M; row++)
	     {
	         if(insert(root, row)) 
	            res++;
	     }
	     
	     return res;
	 }

    
	public static void main(String args[]) 
	{ 
		
		        
		
		
		System.out.println(countDis());
		
	
		
	} 
}
```

