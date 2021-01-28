
// Online IDE - Code Editor, Compiler, Interpreter

public class Main
{
    public static void main(String[] args) {
        int []originalArray = {-1, -2, 2, 0, 4};
		int arraySize = originalArray.length;
        int minValue = originalArray[0];
        int maxValue = originalArray[0];
        int j = 0;
        int lostValue;
        
        //BEGIN FOR LOOP: Finds the minimum and maximum values for the array
        for (int i = 0; i < arraySize; i++){
            if(originalArray[i] < minValue){
                minValue = originalArray[i];
            }
            
            if (originalArray[i] > maxValue){
                maxValue = originalArray[i];
            }
        }
        //END FOR LOOP
        
        
        ///Creates empty sorted and truth arrays for use later. Sets the minimum value for the sorted array
        boolean [] truthArray = new boolean[originalArray.length+1];
        int [] sortedArray = new int[originalArray.length+1];
        sortedArray[0] = minValue;
        
        //START OF FOR LOOP: Creates a sorted array with the values from the original array. Helps keeps track
        //of missing values
	    for(int i = 1; i < sortedArray.length; i++){
	       sortedArray[i] = sortedArray[i-1]+1;
	    }
	    //END OF FOR LOOP
	    
	   ///START OF FOR LOOP: Checks values of sorted array against the original, and updates a corresponding truth array
	   /// with true/false values to keep track of missing value
	   for(int sortedArrayIndex = 0; sortedArrayIndex < sortedArray.length; sortedArrayIndex++){
	       for(int originalArrayIndex = 0; originalArrayIndex < originalArray.length; originalArrayIndex++){
	           if(sortedArray[sortedArrayIndex] == originalArray[originalArrayIndex]){
	               truthArray[sortedArrayIndex] = true;
	               break;
	           }
	           else{
	               truthArray[sortedArrayIndex] = false;
	           }
	       }
	   }
	   ///END of FOR LOOP
	  
	   
	   //BEGIN FOR LOOP: Checks true/false array for a false value. This is the missing value and prints a corresponding
	   // value from the sorted array.
	   for (int truthArrayIndex = 0; truthArrayIndex < truthArray.length; truthArrayIndex++){
	       if(truthArray[truthArrayIndex] == false){
	           System.out.println("The missing value is: " + sortedArray[truthArrayIndex]);
	       }
	   }
	   //END OF FOR LOOP
    }
}
