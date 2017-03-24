
### what is "How to find friend from column"? (Php+Oracle)

I want to find member_no =10002 who is his friends. When I use 

```sql
select * from member where member_no=10002; 
```
the result=> friend_no=10003,10004. But it missed the friend_no=10001. 
<br>

 
![image](https://raw.githubusercontent.com/chliwei199/How-to-find-friend-from-column/master/tablePic.png)



### Solution:

##### First: change sql command, the result => will show like below.

```sql
  SELECT member_no,friend_no
  FROM friend 
  where friend_no=10001 or member_no=10001;
```

![image](https://raw.githubusercontent.com/chliwei199/How-to-find-friend-from-column/master/tablePic2.png)

##### Second: I can get the array like the pic. So use foreach to save 10002's friend to array.

```php
  if(!empty($friends)){
    foreach($friends as $friend){
        if($friend->member_no==10002){
            $friendArray[]=$friend->friend_no;
        }
        elseif($friend->friend_no==10002){
            $friendArray[]=$friend->member_no;
        }
        
    }
  }
```

##### Thus I can get the friends correctly!! 




