
#### 455. Assign Cookies

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

```cpp
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        std::sort(g.begin(), g.end());
        std::sort(s.begin(), s.end());
        int i = 0, j = 0;
        int ret = 0;
        while (i < g.size() && j < s.size())
        {
            if (g[i] <= s[j])
            {
                ++i;
                ++j;
                ++ret;
            }
            else
            {
                ++j;
            }
        }
        return ret;
    }
};
```

#### 1. Two Sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

```cpp
class Solution {
public:
    std::vector<int> twoSum(std::vector<int>& nums, const int target)
    {
        unordered_map<int, int> map{};

        for (int i = 0; i < nums.size(); i++)
        {
            if (map.count(target - nums[i]))
            {
                return {map[target - nums[i]], i};
            }
            map[nums[i]] = i;
        }
        return {-1, -1};
    }
};
```

#### 2. Add Two Numbers

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* p1 = l1;
        ListNode* p2 = l2;
        ListNode* dummy = new ListNode();
        ListNode* sp = dummy;
        int carry = 0;
        while (p1 && p2)
        {
            ListNode* tmp = new ListNode();
            sp->next = tmp;
            sp = sp->next;
            int sum = p1->val + p2->val + carry;
            sp->val = sum % 10;
            carry = sum / 10;
            p1 = p1->next;
            p2 = p2->next;
        }
        while (p1)
        {
            ListNode* tmp = new ListNode();
            sp->next = tmp;
            sp = sp->next;
            int sum = p1->val + carry;
            sp->val = sum % 10;
            carry = sum / 10;
            p1 = p1->next;
        }
        while (p2)
        {
            ListNode* tmp = new ListNode();
            sp->next = tmp;
            sp = sp->next;
            int sum = p2->val + carry;
            sp->val = sum % 10;
            carry = sum / 10;
            p2 = p2->next;
        }
        if (carry == 1)
        {
            ListNode* tmp = new ListNode(1);
            sp->next = tmp;
        }
        return dummy->next;
    }
};
```



