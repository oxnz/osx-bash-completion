CONTRIBUTING
------------

Contributions to the bash completion project are more than
welcome. Fixes, clean-ups and improvements of existing code are much
appreciated, as are completion functions for new commands.

If you wish to contribute code, please bare the following coding
guidelines in mind:

- Do not use Perl, Ruby, Python etc. to do text processing unless the
  command for which you are writing the completion code implies the
  presence of one of those languages.

  For example, if you were writing completion code for perldoc(1), the
  use of Perl to achieve your goal would be acceptable. irb(1)
  completion would similarly make the use of Ruby acceptable.

  Even so, please consider alternatives to these large and slow to
  start interpreters. Use lightweight programs such as grep(1), awk(1)
  and sed(1).

- Use the full power of bash >= 3.2. We no longer support earlier bash
  versions, so you may as well use all the features of that version of
  bash to optimise your code. However, be careful when using features
  added since bash 3.2, since not everyone will be able to use them. Be
  ESPECIALLY careful of using features exclusive to 4.x, as many people
  are still using 3.x.

  For example, extended globs often enable you to avoid the use of
  external programs, which are expensive to fork and execute, so do
  make full use of those:

  ?(pattern-list) - match zero or one occurrences of patterns
  *(pattern-list) - match zero or more occurrences of patterns
  +(pattern-list) - match one or more occurrences of patterns
  @(pattern-list) - match exactly one of the given patterns
  !(pattern-list) - match anything except one of the given patterns

- Following on from the last point, be sparing with the use of
  external processes whenever you can. Completion functions need to be
  fast, so sacrificing some code legibility for speed is acceptable.

  For example, judicious use of sed(1) can save you from having to
  call grep(1) and pipe the output to cut(1), which saves a fork(2)
  and exec(3).

  Sometimes you don't even need sed(1) or other external programs at
  all, though. Use of constructs such as ${parameter#word},
  ${parameter%word} and ${parameter/pattern/string} can provide you a
