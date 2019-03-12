# 算法理论课堂整理
一、计数排序O（n）
  1.找出待排序的数组中最大和最小的元素；
  2.统计数组中每个值为i的元素出现的次数，存入数组C的第i项；
  3.对所有的计数累加（从C中的第一个元素开始，每一项和前一项相加）；
  4.反向填充目标数组：将每个元素i放在新数组的第C(i)项，每放一个元素就将C(i)减去1。
  5.整理算法理论课堂所学，结合LeetCode使用java实现
  
  java代码实现
  public class CountingSort {

    public static void main(String[] args) {
      int[] arrays = new int[] {9,8,7,6,5,4,3};
      System.out.println("待排序："+Arrays.toString(arrays));
      CountSort(arrays);
      System.out.println("排序后："+Arrays.toString(arrays));
    }

    private static int[] CountSort(int[] arrays) {
      if(arrays.length==0)
        return arrays;
      int max = arrays[0],min = arrays[0];
      for(int i=1;i<arrays.length;i++)
      {
        if(arrays[i]>max)
          max = arrays[i];
        if(arrays[i]<min)
          min = arrays[i];
      }
      int[] c = new int[max - min + 1]; 
      Arrays.fill(c, 0);	
      for(int i = 0; i < arrays.length; i++)
        c[arrays[i] - min]++;
      int index = 0,i = 0;
      while(index < arrays.length) {
        if(c[i]!=0) {
          arrays[index] = i + min;
          c[i]--;
          index++;
        }else
          i++;
      }
      return arrays;
    }	
  }
