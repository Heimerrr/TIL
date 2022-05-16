# WYSIWYG

게시판 기능 중 하나 ,
What you See What you Get(보이는 대로 글이 써진다.)의 약자

Medium Editor github: https://github.com/yabwe/medium-editor  
Demo : https://yabwe.github.io/medium-editor/

내가 사용할 WYSIWYG 
https://summernote.org/


### 1. 라이브러리 설치 

(pip install django-ckediter- 파일업데이트 유료이다 . 그래서 아래 무료인 것을 사용)
        
    pip install django-summernote

### 2. INSTALLED_APPS 추가
    INSTALLED_APPS= [ 
        # 생략,
        'django_summernote'
    ]

### 3. urls에 summernote include
    urlspatterns =[
        path('admin/',admin.site.urls),
        path('summernote/', include('django_summernote.urls')),
    ]

### 4. 이미지 업로드 위해 media 설정 진행

    #settings.py
    MEDIA_URL = '/media/'
    MEDIA_ROOW = os.path.join(BASE_DIR,'media/')

### 5. form에 summernote 적용
    class PostForm(forms.ModelForm):
    class Meta:
        model = Post
        fields = ['subject','message']
        widgets= {
            'message': SummernoteWidget(),

        }
        labels={
            'subject' : "",
            'message' : "",
        }