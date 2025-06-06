﻿---
layout: default
title: Partition-Linked-List
narrow: true
---
Given a linked list and a target value T, partition it such that all nodes less than T are listed before the nodes larger than or equal to target value T. The original relative order of the nodes in each of the two partitions should be preserved.

**Examples**
- L = 2 -> 4 -> 3 -> 5 -> 1 -> null, T = 3, is partitioned to 2 -> 1 -> 4 -> 3 -> 5 -> null

***

- Step1: 设置两个dummy node
- Step2：将大于和小于target的节点接到两个dummy node上
	- 牢记：先保存下一个节点
```java
  public ListNode partition(ListNode head, int target) {
    ListNode dummy1 = new ListNode(0);
    ListNode cur1 = dummy1;
    ListNode dummy2 = new ListNode(0);
    ListNode cur2 = dummy2;
    while(head != null){
      if (head.value < target){
        cur1.next = head;
        cur1 = cur1.next;
      }else{
        cur2.next = head;
        cur2 = cur2.next;
      }
      head = head.next;
    }
    cur1.next = dummy2.next;
    cur2.next = null;
    return dummy1.next;
  }
```