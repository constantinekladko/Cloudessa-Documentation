# Cloudessa RADIUS Manual

## Chapter 1: 60 second lessons

### Lesson 0: Create a user and a group.

Lets create a group of RADIUS users, and add at least one user to this group. You'll need this for all other lessons.

First create a user

* Go to `Users` and click `Create`
* Specify login as `test` and password as `test123456`
* Click OK

Now create a group

* Go to `User Groups` and click `Create`
* Specify name as `Group1`
* Click OK

Now add the user to the group

* Select `Group1`
* Go to `Users` tab.
* Click `Add user` and select user `test` 
* Click OK


Now we have created user `test` which is a member of `Group1`. 


### Lesson 1: Create a simple PAP server

Lets create a simple authentication server that implements PAP protocol.

First lets create a virtual server

* Go to `Virtual Servers`, click `Create`
* In the pop-up windows set server name to `PAP Server` and protocol to `PAP`.
* Click `OK`. Now the server is created.
* Now click the server to see the IP address as well as the authentication and accounting port numbers for the server. You need this information to configure your RADIUS client.

Now lets create a user, a group, add the user to the group 





*View the [source of this content](http://github.github.com/github-flavored-markdown/sample_content.html).*

Let's get the whole "linebreak" thing out of the way. The next paragraph contains two phrases separated by a single newline character:

Roses are red
Violets are blue

The next paragraph has the same phrases, but now they are separated by two spaces and a newline character:






What about some code **in** a list? That's insane, right?

1. In Ruby you can map like this:

        ['a', 'b'].map { |x| x.uppercase }

2. In Rails, you can do a shortcut:

        ['a', 'b'].map(&:uppercase)

Some people seem to like definition lists

<dl>
  <dt>Lower cost</dt>
  <dd>The new version of this product costs significantly less than the previous one!</dd>
  <dt>Easier to use</dt>
  <dd>We've changed the product so that it's much easier to use!</dd>
</dl>

I am a robot
------------

Maybe you want to print `robot` to the console 1000 times. Why not?

    def robot_invasion
      puts("robot " * 1000)
    end

You see, that was formatted as code because it's been indented by four spaces.

How about we throw some angle braces and ampersands in there?

    <div class="footer">
        &copy; 2004 Foo Corporation
    </div>

Set in stone
------------

Preformatted blocks are useful for ASCII art:




Or perhaps someone a little less eloquent:

> I wish you'd have given me this written question ahead of time so I
> could plan for it... I'm sure something will pop into my head here in
> the midst of this press conference, with all the pressure of trying to
> come up with answer, but it hadn't yet...
>
> I don't want to sound like
> I have made no mistakes. I'm confident I have. I just haven't - you
> just put me under the spot here, and maybe I'm not as quick on my feet
> as I should be in coming up with one.

Table for two
-------------

<table>
  <tr>
    <th>ID</th><th>Name</th><th>Rank</th>
  </tr>
  <tr>
    <td>1</td><td>Tom Preston-Werner</td><td>Awesome</td>
  </tr>
  <tr>
    <td>2</td><td>Albert Einstein</td><td>Nearly as awesome</td>
  </tr>
</table>

Crazy linking action
--------------------

I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

  [1]: http://google.com/        "Google"
  [2]: http://search.yahoo.com/  "Yahoo Search"
  [3]: http://search.msn.com/    "MSN Search"