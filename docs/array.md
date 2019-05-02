# array

## kth smallest element using quickselect
1. avg time complexity O(nlogn)
```c++
class Solution {
public:
    vector<int> nums;
    int findKthLargest(vector<int>& nums, int k) {
        this->nums = nums;
       int size = nums.size();
       return quickselect(0, size - 1, size - k);
    }
    
    
    int partition(int left, int right, int pivot_index) {
        int pivot = nums[pivot_index];
        // 1. move pivot to end
        swap(nums[pivot_index], nums[right]);
        int store_index = left;

        // 2. move all smaller elements to the left
        for (int i = left; i <= right; i++) 
          if (this->nums[i] < pivot) 
            swap(nums[store_index++], nums[i]);

        // 3. move pivot to its final place
        swap(nums[store_index], nums[right]);

        return store_index;
  }
    
    int quickselect(int left, int right, int k_smallest) {
    /*
    Returns the k-th smallest element of list within left..right.
    */

    if (left == right) // If the list contains only one element,
      return this->nums[left];  // return that element

    // select a random pivot_index
 
    int pivot_index = left + rand()%(right - left); 
    
    pivot_index = partition(left, right, pivot_index);

    // the pivot is on (N - k)th smallest position
    if (k_smallest == pivot_index)
      return this->nums[k_smallest];
    // go left side
    else if (k_smallest < pivot_index)
      return quickselect(left, pivot_index - 1, k_smallest);
    // go right side
    return quickselect(pivot_index + 1, right, k_smallest);
  }
    
};
```
