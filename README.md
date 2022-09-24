# MaxHeap-C#
Implementation Of MaxHeap using C#
using System;
using System.Collections.Generic;
using System.Text;

namespace DataStructure
{
    public class MaxHeap
    {
        public IList<int> maxHeap = new List<int>();

        public int peek()
        {
            if (maxHeap.Count < 1) return -1;
            return maxHeap[0];
        }

        public int size()
        {
            if (maxHeap.Count < 1) return 0;
            return maxHeap.Count;
        }

        public void add(int item)
        {
            maxHeap.Add(item);
            upheapify(maxHeap.Count - 1);
        }

        public int remove()
        {
            if (maxHeap.Count < 1) return -1;

            int val = maxHeap[0];
            swap(0, maxHeap.Count - 1);
            maxHeap.RemoveAt(maxHeap.Count - 1);
            downHeapify(0);
            return val;
        }

        private void downHeapify(int i)
        {
            int max = -1;
            int left = 2 * i + 1;
            
            if(maxHeap[left] > maxHeap[i])
            {
                max = left;
            }

            int right = 2 * i + 2;

            if (maxHeap[right] > max)
            {
                max = right;
            }

            if(max != -1)
            {
                swap(max, i);
                downHeapify(max);
            }

        }

        private void upheapify(int i)
        {
            if (i == 0) return;

            int parentIndex = (i - 1) / 2;

            if(maxHeap[parentIndex] < maxHeap[i])
            {
                swap(i, parentIndex);
                upheapify(parentIndex);
            }

        }

        private void swap(int index1, int index2)
        {
            int temp = maxHeap[index1];
            maxHeap[index1] = maxHeap[index2];
            maxHeap[index2] = temp;
        }


    }
}
