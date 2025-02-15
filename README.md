# Leetcode----2698
Find the Punishment Number of an Integer
//code in java
public class Solution {
    public int punishmentNumber(int n) {
        int totalSum = 0;
        for (int i = 1; i <= n; i++) {
            int square = i * i;
            if (canPartition(Integer.toString(square), i)) {
                totalSum += square;
            }
        }
        return totalSum;
    }

    private boolean canPartition(String numStr, int target) {
        return canPartitionHelper(numStr, target, 0, 0);
    }

    private boolean canPartitionHelper(String numStr, int target, int start, int currentSum) {
        if (start == numStr.length()) {
            return currentSum == target;
        }
        for (int end = start + 1; end <= numStr.length(); end++) {
            int part = Integer.parseInt(numStr.substring(start, end));
            if (canPartitionHelper(numStr, target, end, currentSum + part)) {
                return true;
            }
        }
        return false;
    }
}
