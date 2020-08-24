#### [2. 两数相加](https://leetcode-cn.com/problems/add-two-numbers/)

![image-20200824155459312](http://akatsuke.com/image-20200824155459312.png)

```go
//go语言题解

type ListNode struct {
    Val int
    Next *ListNode
}

func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
    Head := &ListNode{Val: -1, nil}
    tmp, status := Head, false
    for l1 != nil || l2 != nil || status {
        sum := 0
        if status {
            sum += 1
            status = false
        }
        if l1 != nil {
            sum += l1.Val
            l1 = l1.Next
        }
        if l2 != nil {
            sum += l2.Val
            l2 = l2.Next
        }
        if sum >= 10 { status = true }
        sum %= 10
        tmp.Next = &ListNode{Val: sum}
        tmp = tmp.Next
    }
    return Head.next
}
```

