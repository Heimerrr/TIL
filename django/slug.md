# slug란
일반적으로 이미 얻은 데이터를 사용하여 유효한 URL을 생성하는방법  
예를들어, Slug는 기사 제목을 사용하여 URL을 생성  
수동으로 설정하는 대신 제목 (혹은 다른 데이터)가 주어지면 함수를 통해 슬러그를 생성하는게 좋다.

### 예시
~~~
<title> The 46 Year Old Virgin </title>
<content> A silly comedy movie </content>
<slug> the-46-year-old-virgin </slug>
~~~
있다고 가정하면 
~~~
class Article(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField(max_length=1000)
    slug = models.SlugField(max_length=40)
~~~
www.example.com/article/13 -> wwww.example.com/article/the-46-year-old-virgin 
이렇게 대체가 가능하다.


## <spen style="color:red">하지만, Slug는 단일성(Uniqueness)를 보장하지 않기때문에 다음과 같이 URL을 사용하는게 현명하다.</span>