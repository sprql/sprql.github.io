---
layout:  post
title:   "tomlresume"
date:    2017-02-12 00:00:00 +0000
excerpt: "TOML-based standard for resumes"
---

There are many formats for creating a resume.
Some formats are easy to parse, some other are easy to read.

To combine both properties usually use a machine readable format which is easy to convert to human-readable.

[JSON Resume] specification allows you to describe your resume in JSON, which is easy to parse and classify and easily create HTML, or even PDF version.

However, to write your resume in JSON is not so easy, too much syntactical noise, and it's much easier to use some UI/app for this.

But there is a more interesting option is to use [TOML] as resume format.

> TOML aims to be a minimal configuration file format that's easy to read due to obvious semantics.

It is easy to parse, write, and read.

So if you plan to update your resume is a good time to create your resume in the TOML format.

And to simplify the work you can use project [tomlresume].

[tomlresume] contain a TOML-based resume template (compatible with [JSON Resume Schema]), and tools to create HTML and JSON formats as well.


[JSON Resume]: https://jsonresume.org
[TOML]: https://github.com/toml-lang/toml
[tomlresume]: https://github.com/sprql/tomlresume
[JSON Resume Schema]: https://github.com/jsonresume/resume-schema