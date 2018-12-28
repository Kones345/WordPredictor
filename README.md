# Solution

#### Word.java
To make checking where complete words exist in my tree and the popularity of these objects, I store a word object in each dictionary tree which simply stores the full word which was inserted and potentially it's popularity. The word object implements the comparator interface so that I can sort a collection of words based on their popularity later based on their popularity. The complete word and popularity values are set to empty optionals initially to avoid null pointers.

#### Size
My initial size implementation defines an initial size variable as 1 for each dictionary tree. And loops through each child in the dictionary tree and recursively adds the result of the size function for each node.
With folding, we fold by adding each value in the collection of integers to the size and adding one to it for the current node. The result of this fold is passed to the collection in the fold on the level above on each recursive step and therefore allows us to calculate the size.

#### Height
My initial implementation defines the initial height variable as -1. After this, we loop through each of the children for the current dictionary tree and recursively call the height method and assign the height of the current node to the maximum of the current height value and the height of its children. With folding, this works by looping through each member of the collection and returning the maximum of the current height value and the node and each result from the collection of heights on the previous level. At the end of the function, we then return this height value plus one.

#### Maximum Branching
My initial implementation defines an initial maximum value as the minimum possible integer. For each child in each dictionary tree, we loop through the children and assign the maximum value for the current node to the maximum of the current maximum value at this node and the size of the dictionary tree in the child we are looping over. When we are folding, this works by again, defining the maximum value initially as the minimum possible integer; after we iterate over every value in the collection which we receive and find the maximum of the size of the children at the current dictionary tree and maximum values found at lower levels in the tree. We then return the maximum result.

#### Longest Word
To find the longest word, at each level I check which child in a dictionary tree has the greatest height. I then return the string of the character + the recursive call on the tree attached to this character of the greatest character. When we get to the end of the string we return an empty string. As a result, the method will concatenate a character from the longest word at each level.

#### Number of Leaves
My initial implementation initially sets a value for the number of leaves in each dictionary tree as 0. If the number of children in the current dictionary tree was 0 then we would set it to 1 and add to this result of the number of leaves function in each of the children of the current dictionary tree.
When folding, this works by setting an initial number of leaves value for each tree. We append each value in the collection passed to the fold function to the number of leaves and if the children for this node are empty then we add one to the number of leaves and return this result.

#### Contains
To check if a word is contained in the tree, if the length of the word is 1, then we get the tree which is attached to this key in the current tree's children if the letter is contained. We check this tree for whether or not the complete word object is empty. If it is empty, then we return false, otherwise true.

#### All Words
To get all words from the tree, I define an initial list which we will return all the words in. If the current dictionary tree has a complete word present then we add it to the list. After this, We loop through each of the children and add the result of all words to our first array list. After this, we return the final array list which will contain all the results.

#### Insert
To insert a word into the tree, I check if the letter exists, I use a helper function to take the current potion of the word we are looking at and the full word so that we can set the complete word variable in the word object. We first check if the first letter is contained in the top level dictionary tree of children, if it is not then we insert the character with a new dictionary tree which we insert the rest of the word into. If the letter is already there, then we get the tree which is attached to this already existing character and insert the rest of the word into this tree. When the length of the portion of the word we are inserting has a length of 1, we know that we are at the end of the word to insert. This means that we get the dictionary tree for this character (if it exists - if not we will create a new dictionary tree) and set the complete word (and popularity when it applies) to the values passed into the parameters.

#### Remove
To remove a word from the tree, I first check if it is contained, in the tree, if not then return false. Otherwise, I try to remove each character of the word one by one starting from the back. As a result, I use a for-loop which iterates from the last character in the word to the first character and calls a removal helper method. The helper method goes from the start of the word to the end of the current portion of the word we are trying to remove. If the complete word variable has already been set and it is equal to what we want to remove, then we check whether or not the corresponding tree has children or not. If it does then we simply set the Word objects to empty; otherwise, we remove this entry and its corresponding tree from the map of children in the tree. If the letter we are trying to remove is not the last one, any complete words we find will be from another word, hence we don't want to do anything. If we find a letter who's tree has no complete word and there are no children below, we remove this entry from the map of children in the dictionary tree. 

#### Predict
To predict a word given a prefix, if the prefix is contained in the tree then we traverse the tree until we get to the end of the current prefix. From here, I call the allWords() method on the subtree below the end of the prefix and choose the first entry which is given in the list.
When predicting with popularity, I do the same except that when I call allWords(), I sort all the entries which are returned by their popularity value and return the first n values. If there are less than n words then I just return everything.

#### Fold
To implement the fold function I largely followed the instructions followed in the comments. I created a new ArrayList to store all the results of folding. After this, I loop through all the children in the current tree and fold each child, and add the result of this fold to the ArrayList of results. After this, I apply the BiFunction passed to the current dictionary tree and the ArrayList of results and the collection of As I have just created. 





