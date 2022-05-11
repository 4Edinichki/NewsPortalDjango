from news.models import *

u1 = User.objects.create_user(username='user_1')
u2 = User.objects.create_user(username='user_2')

Author.objects.create(user=u1)
Author.objects.create(user=u1)

Category.objects.create(name='Sport')
Category.objects.create(name='Education') 
Category.objects.create(name='Hobby')     
Category.objects.create(name='Work')  

Post.objects.create(author=Author.objects.get(id=3), category_news='AR', heading_news='First article', text_news='Text in first article')
Post.objects.create(author=Author.objects.get(id=4), category_news='AR', heading_news='Second article', text_news='Text in second article')
Post.objects.create(author=Author.objects.get(id=3), category_news='NW', heading_news='First news', text_news='Text in first news')

Post.objects.get(id=6).category.add(Category.objects.get(id=6))
Post.objects.get(id=6).category.add(Category.objects.get(id=5)) 
Post.objects.get(id=7).category.add(Category.objects.get(id=7)) 
Post.objects.get(id=8).category.add(Category.objects.get(id=8))

Comment.objects.create(post=Post.objects.get(id=6), user=u1, text_comment='This article very good!') 
Comment.objects.create(post=Post.objects.get(id=7), user=u1, text_comment='Bad article')             
Comment.objects.create(post=Post.objects.get(id=8), user=u1, text_comment='Bad news')    
Comment.objects.create(post=Post.objects.get(id=6), user=u2, text_comment='Good article') 

Comment.objects.get(id=5).like()
Comment.objects.get(id=6).like()
Comment.objects.get(id=7).dislike()
Post.objects.get(id=6).like()
Post.objects.get(id=7).like()
Post.objects.get(id=8).dislike()

Author.objects.get(id=3).update_raiting()
Author.objects.get(id=4).update_raiting()

Author.objects.order_by('-range_author')[:1] 
for i in a:
...     i.range_author
...     i.user.username

 for i in Post.objects.order_by('-rang_news')[:1]: 
...     i.time_add_news
...     i.author         
...     i.rang_news                                   
...     i.heading_news
...     i.preview()

for i in Comment.objects.all():
...     i.time_add_comment          
...     i.user.username
...     i.rang_comment



