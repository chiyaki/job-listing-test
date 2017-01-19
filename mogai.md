# 目标：

* 首页美化
* 管理员后台美化

## Part 1: 首页美化

### Step 0: 把welcome/index设为首页

```ruby routes.rb
- root 'jobs#index'
+ root 'welcome#index'
```

### Step 1: 在首页加个头图

```ruby welcome/index.html.erb
- <h1> Hello World! <h1>

+  <div class="jumbotron">
+    <h1 class="title">18K Offer</h1>
+    <p class="slogan">18K Offer 是一个提供18K薪水工作机会的求职网站。
+    <br>
+    我们希望藉由这个网站，能让大家找到且应征上高薪且优质的工作。
+    <br>
+     凭借自己的努力和天份也会变 Winner
+    </p>
+    <p class="lead"><a class="btn btn-lg btn-danger" href="/jobs">马上应征</a></p>
+  </div>
```

```ruby app/assets/stylesheets/application.scss
.jumbotron {
  background-image:url('http://y.photo.qq.com/img?s=n0m7YMg0L&l=y.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  padding-bottom: 110px;
}

.title {
  font-family: "Helvetica Neue", "Microsoft Yahei", 微软雅黑;
  text-align: center;
  margin-top: 200px;
  margin-bottom: 80px;
}

.slogan {
  margin-top: 10px;
  margin-bottom: 50px;
  text-align: center;
  color: white;
  top: 12px;
}

.lead {
  margin-bottom: 60px;
  text-align: center;
  color: white;
}
```

### Step 2: 在头图下方加入其他信息
```ruby welcome/index.html.erb
<section id="company">
  <div class = "container-fluid">
    <div class="row">
      <div class="col-sm-4 ">
        <div class="thumbnail">
          <img src="http://y.photo.qq.com/img?s=VfqbvmFVI&l=y.jpg" alt="search" class = "img-thhumbnail">
          <div class="caption">
            <h3>北京朝阳建外SOHO</h3>
          </div>
        </div>
      </div>
      <div class="col-sm-4 ">
        <div class="thumbnail">
          <img src="http://y.photo.qq.com/img?s=9yBkCQVj7&l=y.jpg" alt="bid" class = "img-thhumbnail">
          <div class="caption">
            <h3>info@18koffer.com</h3>
          </div>
        </div>
      </div>
      <div class="col-sm-4 ">
        <div class="thumbnail">
          <img src="http://y.photo.qq.com/img?s=bAQJ8dfF4&l=y.jpg" alt="heart" class = "img-thhumbnail">
          <div class="caption">
            <h3>010-12344321</h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
```
```ruby app/assets/stylesheets/application.scss
.caption {
  margin: 30px;
  text-align: center;
  top: 20px;
}

.thumbnail {
    border: 0 none;
    box-shadow: none;
    margin-top: 60px;
}
```
![](https://ww1.sinaimg.cn/large/006tNc79ly1fbvwdv91scj311n17h4fh.jpg)
<br/>
## Part 2: 管理员后台美化
### Step 1:更改按钮样式
```ruby app/views/admin/jobs/index.html.erb
<td>
-    <%= link_to("Edit", edit_admin_job_path(job)) %>
-    | <!-- 有了按钮以后就不需要竖分割线 -->
+    <%= link_to("Edit", edit_admin_job_path(job), :class => "btn btn-xs btn-info") %> <!-- "btn btn-xs btn-info"为bootstrap语法 -->
-    <%= link_to("Destroy", admin_job_path(job), :method => :delete, :class => "btn btn-xs btn-default info", :data => { :confirm => "Are you sure?" }) %>
-    |
+    <%= link_to("Destroy", admin_job_path(job), :method => :delete, :class => "btn btn-xs btn-danger", :data => { :confirm => "Are you sure?" }) %>
     <% if job.is_hidden %>
-      <%= link_to("Publish", publish_admin_job_path(job) , :method => :post, :class => "btn btn-xs btn-default ") %>
+   <%= link_to("Publish", publish_admin_job_path(job) , :method => :post, :class => "btn btn-xs btn-success") %>
    <% else %>
-    <%= link_to("Hide", hide_admin_job_path(job), :method => :post,  :class => "btn btn-xs btn-default") %>
+   <%= link_to("Hide", hide_admin_job_path(job), :method => :post,  :class => "btn btn-xs btn-warning") %>
    <% end %>
</td>
```
### Step 2: 更改表格样式
```ruby app/views/admin/jobs/index.html.erb
- <table class="table table-boldered" >
+ <table class="table table-boldered table-striped custab" >
```
```ruby app/assets/stylesheets/application.scss
.custab{
  border: 1px solid #ccc;
  padding: 5px;
  margin: 5% 0;
  box-shadow: 3px 3px 2px #ccc;
  transition: 0.5s;
}

.custab:hover{
  box-shadow: 3px 3px 0px transparent;
  transition: 0.5s;
}
```
![](https://ww2.sinaimg.cn/large/006tNc79ly1fbvwf1db4sj30z10ecwft.jpg)

### Step 3: git 存档

```
git add .
git commit -m "better welcome/index & admin/jobs/index"
```
