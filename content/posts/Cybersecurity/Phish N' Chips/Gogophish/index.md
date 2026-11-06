---
title: Gogophish - Turning Gophish into a Command Line Utility
date: 2026-11-05T21:43:59-05:00
menu:
  sidebar:
    name: Intro to Gogophish
    identifier: gogophish-intro
    parent: phishnchips
    weight: 20
author:
  name: Pete Cipolone
  image: /images/author/john.png
---

# Introducing gogophish: A Command-Line Tool for Gophish

I wanted to use this blog post to introduce **gogophish**, a command-line tool to interact with the [Gophish](https://getgophish.com) phishing framework. This tool is the result of the many lessons learned during social engineering pentests. It started out as a small program to do one thing, and additional features were added over time to solve problems and add flexibility.

This post covers the basic functionality of the tool, some of its more unique features, and a couple of use cases where it really excels. Enjoy!

## Under the Hood

gogophish is a Go program that uses the Gophish API to interact with Gophish, the phishing framework. Access is established by configuring the `config.yaml` file with the Gophish API key and URL. Once access is established, the utility can do the following:

- Create / send / list / delete **campaigns**
- Upload / download / list / delete **user groups**
- Upload / download / list / delete **phishing email templates**
- Create / list **sending profiles**

In addition to these standard features, gogophish offers some unique features to solve issues discovered during phishing assessments and to speed up the workflow.

### Migrate

The **migrate** feature lets you specify a second Gophish instance in the config file and transfer all email templates, user groups, and sending profiles from one instance of Gophish to another. This is helpful when you need to switch from the Evilginx version of Gophish to the original version of Gophish (no, they are not the same). It's also handy if you don't have a dedicated Gophish server and spin up a new one for each client.

### Convert

The **convert** feature lets you specify a `.txt` file of emails (or pipe from stdin), format it into a proper `.csv`, and upload it to Gophish. Often when a client has a list of users they want targeted, its just a list of emails. This saves you from manually converting the file to `.csv` and uploading it. It's also convenient when you're sourcing emails from another utility; it's easier to save a tool's output to a `.txt` file or pipe it directly into gogophish.

### Split

The **split** feature takes a group of users and splits it into the number of groups you want. Just specify the group, and gogophish will download it, split it, and reupload the smaller groups for you.

## Use Cases

### 1. Resending a phishing email while testing inbox behavior

You're testing out a new phishing email and observing how it behaves when it lands in the inbox. Copying the campaign to resend it multiple times in the GUI takes time. The `copy` command clones a campaign and automatically increments the trailing number in its name, so you only have to hit the up arrow to generate a new one:

```bash
gogophish campaign copy "InboxTest-1"

```

### 2. Cleaning up all those test campaigns

Remember all those campaigns you made in the first use case? You can easily list them and then delete them with a single wildcard pattern so they aren't clogging up the campaign list. You can specify an exact name, wildcard, or campaign ID. 

```bash
gogophish campaign list                      # see what you made
gogophish campaign delete "InboxTest*" -y    # wildcard deletes them all; -y skips the prompt
```

### 3. Sending the client the list of users you're about to phish

Did the client just ask which users you are about to phish? You can download the user list to a text file and send it over to them:

```bash
gogophish group emails "example group" -o users.txt
```

### 4. Generating a customized Word document per client

Are you doing something unusual like subdocument injection, where every client needs their own customized Word document? This can be done in a bash loop: create a template per client, each carrying its own crafted `.docx`:

```bash
for client in example, example2, example3; do
  gogophish template create "SubdocInject-${client}" \
    --subject "Invoice for ${client}" \
    --html-file ./body.html \
    --attachment "./docs/${client}.docx"
done
```

If you'd rather swap the attachment on a single existing template instead of creating many, use:

```bash
gogophish template update "SubdocInject" \
  --clear-attachments \
  --attachment "./docs/${client}.docx"
```

### 5. Default Flexibility

Because this makes Gophish a command-line utility, it can be used in combination with bash scripts and other programming languages.
