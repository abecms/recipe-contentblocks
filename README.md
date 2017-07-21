# recipe-contentblocks
This recipe shows you how to create repetable blocks of content

![Screenshot](/site/screenshot.jpg?raw=true)


## Introduction
Creating repetable blocks of content is quite easy. You'll find 2 examples inspired by http://tedxcannes.com/videos/2016/ and http://tedxcannes.com/equipe

## How to
To create a repetable block of content, we'll use the handlebars tag ```{{#each name}}```
Inside such a block, you'll be able to define abe tags. For an abe tag to be repetable, it has to be inside an {{#each name}} block and its key attribute must begin with the name used in the each:

```
<ul class="team-items primary group">
  {{#each team}}
  <li class="team-item group">
    <div class="info-side">
      <h4 class="name">
        {{abe type='text' key='team.name' desc='name' tab='default' reload='true'}}
        <small class="funtion">
          {{abe type='text' key='team.position' desc='position' tab='default' reload='true'}}
        </small>
      </h4>
      {{#if linkedin}}
      <div class="links">
        <a class="linkedin-link" href="{{abe type='text' key='team.linkedin' desc='linkedin' tab='default' reload='true'}}" target="_blank">
          LinkedIn
        </a>
      </div>
      {{/if}}
    </div>
    <div class="photo-side">
      <img class="img-responsive" src="{{abe type='image' key='team.photo' desc='photo' thumbs='200x200' tab='default' reload='true'}}">
    </div>
    <div class="border"></div>
  </li>
  {{/each}}
</ul>
```
Here, the ```{{#each team}}``` block defines the "team" object.
Then in the key of the abe tags included in the structure you'll create, you start your key name with "team." like in "team.name".


In this example, you can see that we use an ```{{#if linkedin}}```statement. Why didn't we used ```{{#if team.linkedin}}```?
It's because of the way handlebars works: When you'll test and display values of content blocks, you'll have to remove the head attribute (don't use "team" here) because handlebars does it for you. In the Abe tags, however, you'll have to use this head value in your key attributes.
