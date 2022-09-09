
# This is public data from [atariemailarchive.org](https://atariemailarchive.org)

This repository contains parsed and threaded email data from Jed Margolin's time as a hardware engineer at Atari.

This data backs [atariemailarchive.org](https://atariemailarchive.org), which curates and showcases Jed's emails. The raw email data are in text files on [Jed's website](http://www.jmargolin.com/vmail/vmail.htm), where you can read more about his time there.

You can [read about how I made atariemailarchive.org here](https://vikramoberoi.com/how-i-made-atariemailarchive-org/).

There are 4,128 messages and 2,846 threads in the archive.


## How is this data different from the text files on Jed's website?

* It's parsed.
  * Here's an example of what the raw data looks like: http://www.jmargolin.com/vmail/Vax88.txt
* It has conversation threads.
  * I read all 4,128 emails in the archive and threaded them manually. No, really I did. Yes, you're welcome.

From my correspondence with Jed:

> Did Vaxmail have the notion of conversation threads? And is there any way I can glean them from the raw data? Did, perhaps, the UI default to Re: (subject) when replying to other mail (which would give me an approximation)?
> 
> ---
>
> No, I don't think there were threads. It probably hadn't been invented yet so it wouldn't be in the raw data. In fact, I don't think there was raw data, just ASCII text. And there wasn't much of a UI. It was just text.

I read every single message. If a message was clearly a reply to a prior messages then I added them to the same thread. If you find obvious errors, let me know.


## What's the schema?

There's one `messages` table with the following columns:

* `id`: the primary key, an id for each message
* `thread_id`: messages that belong to the same thread have the same `thread_id`
  * Messages in each thread are ordered by `sent_at`.
* `sender`: the sender of the message in the original `{VAX_NAME}:{USER}` form (more on this below)
* `recipient`: the recipient of the messsage in the original `{VAX_NAME}:{USER}` form (more on this below)
* `cc`: any cc'ed recipients (more on this below)
* `sent_at`: the time the message was sent
* `subject`: the message subject
* `body`: the message body

## How are senders, recipients, and CC formatted?

From my correspondence with Jed:

> Most to: and from: fields are two words with a colon separating them. What do the first and second refer to? In cases where there is no colon delimiter, what does that mean?
> 
> ---
>
> An email like:
>  
> From: KIM::DROBNY       "Buddy Flyback" 29-JAN-1986 10:08:49.22
> To:   @SYS$MAIL:JUNK
>  
> came from the VAX named Kim from user Drobny (Chris Drobny). Chris was a tech and a really good guy. “Buddy Flyback” was his chosen nickname.
>  
> We started with one Vax but when we got a second one they needed names. The new one was Kim (New Vax; from actress Kim Novak). The second one was Ernie (Slow Vax; from famous comedian Ernie Kovax.).
>  
> I’m not sure why some don’t have a colon. It might be where both sender and recipient are on the same Vax.
>  
> @SYS$MAIL:JUNK was a mail distribution list called JUNK, where you could post anything, like what flavor Jello was for lunch that day.

Here are three messages from the archive that may also help you understand what is going on.

* [What the #@%^ is SYS$MAIL?](https://atariemailarchive.org/thread/on-how-to-use-atari-s-mail-distribution-lists-31)
* [A neat trick with mail](https://atariemailarchive.org/thread/on-a-clever-email-hack-19)
* [A list of MAIL lists](https://atariemailarchive.org/thread/a-list-of-mail-lists-294)

## License

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png)](http://creativecommons.org/licenses/by/4.0/)
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

## Author

This dataset is published by [Vikram Oberoi](https://www.twitter.com/voberoi).
