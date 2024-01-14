# Ruby 3.3 on fly.io segfault

Running this app with 256MB RAM will cause a segfault.

Launch the app and make sure you choose 256 MB for your machines RAM.

```
fly launch --vm-memory 256
```

Log:

```
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info] INFO Starting init (commit: 8995e367)...
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info] INFO Preparing to run: `bundle exec rackup --host 0.0.0.0 --port 8080` as ruby
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info] INFO [fly api proxy] listening at /.fly/api
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]2024/01/14 13:01:47 listening on [fdaa:0:5b8f:a7b:273:31b9:ec96:2]:22 (DNS: [fdaa::3]:53)
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/ruby/site_ruby/3.3.0/rubygems.rb:165: [BUG] Segmentation fault at 0xffffffffffffffff
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]ruby 3.3.0 (2023-12-25 revision 5124f9ac75) [x86_64-linux]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]-- Control frame information -----------------------------------------------
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]c:0005 p:0074 s:0023 e:000021 CLASS  /usr/local/lib/ruby/site_ruby/3.3.0/rubygems.rb:165
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]c:0004 p:0045 s:0019 e:000018 TOP    /usr/local/lib/ruby/site_ruby/3.3.0/rubygems.rb:115 [FINISH]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]c:0003 p:---- s:0012 e:000011 CFUNC  :require
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]c:0002 p:0012 s:0007 e:000006 TOP    <internal:gem_prelude>:2 [FINISH]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]c:0001 p:0000 s:0003 E:0000a0 DUMMY  [FINISH]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]-- Ruby level backtrace information ----------------------------------------
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]<internal:gem_prelude>:2:in `<internal:gem_prelude>'
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]<internal:gem_prelude>:2:in `require'
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/ruby/site_ruby/3.3.0/rubygems.rb:115:in `<top (required)>'
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/ruby/site_ruby/3.3.0/rubygems.rb:165:in `<module:Gem>'
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]-- Threading information ---------------------------------------------------
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]Total ractor count: 1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]Ruby thread count for this ractor: 1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]-- Machine register context ------------------------------------------------
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info] RIP: 0x00007f1206ab4664 RBP: 0x00007f1204eaf050 RSP: 0x00007ffdcbefe038
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info] RAX: 0xffffffffffffffff RBX: 0x00007f1204eaf3e8 RCX: 0x00007f1204eaf3e9
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info] RDX: 0xffffffffffffffff RDI: 0x000055c7171520c0 RSI: 0x000000000000c2e3
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]  R8: 0x0000000000000000  R9: 0x000055c717361770 R10: 0x0000000000000001
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info] R11: 0x00007f1204e67f90 R12: 0x00007f1206e40900 R13: 0x0000000000000001
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info] R14: 0x00007f1204eaf550 R15: 0x00007f1204e67f90 EFL: 0x0000000000010202
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]-- C level backtrace information -------------------------------------------
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_print_backtrace+0x14) [0x7f1206b6a23b] /usr/src/ruby/vm_dump.c:820
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_vm_bugreport) /usr/src/ruby/vm_dump.c:1151
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_bug_for_fatal_signal+0x100) [0x7f1206964a80] /usr/src/ruby/error.c:1065
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(sigsegv+0x4b) [0x7f1206ab698b] /usr/src/ruby/signal.c:926
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/lib/x86_64-linux-gnu/libc.so.6(0x7f12064ebfd0) [0x7f12064ebfd0]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_new+0x2c) [0x7f1206ab4664] /usr/src/ruby/shape.c:148
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_insert_aux) /usr/src/ruby/shape.c:247
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_color+0x0) [0x7f1206ab49df] /usr/src/ruby/shape.c:287
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_red_p) /usr/src/ruby/shape.c:111
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_insert) /usr/src/ruby/shape.c:289
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors) /usr/src/ruby/shape.c:434
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors+0x15) [0x7f1206ab49bd] /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors) /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors+0x15) [0x7f1206ab49bd] /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors) /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors+0x15) [0x7f1206ab49bd] /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors) /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors+0x15) [0x7f1206ab49bd] /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors) /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors+0x15) [0x7f1206ab49bd] /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(redblack_cache_ancestors) /usr/src/ruby/shape.c:431
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_shape_alloc_new_child+0x8) [0x7f1206ab5908] /usr/src/ruby/shape.c:473
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(get_next_shape_internal) /usr/src/ruby/shape.c:529
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_shape_get_next) /usr/src/ruby/shape.c:721
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(general_ivar_set+0x4d) [0x7f1206b31a10] /usr/src/ruby/variable.c:1513
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_class_ivar_set) /usr/src/ruby/variable.c:4236
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_ivar_set+0x83) [0x7f1206b31bf3] /usr/src/ruby/variable.c:1844
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(vm_exec_core+0x8ca) [0x7f1206b4deaa] /usr/src/ruby/vm_insnhelper.c:1639
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_vm_exec+0x179) [0x7f1206b53589] /usr/src/ruby/vm.c:2486
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(load_iseq_eval+0x3d) [0x7f12069d658f] /usr/src/ruby/load.c:774
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(require_internal) /usr/src/ruby/load.c:1281
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_require_string_internal+0x34) [0x7f12069d7226] /usr/src/ruby/load.c:1380
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_require_string) /usr/src/ruby/load.c:1373
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(vm_cfp_consistent_p+0x0) [0x7f1206b3c3b9] /usr/src/ruby/vm_insnhelper.c:3490
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(vm_call_cfunc_with_frame_) /usr/src/ruby/vm_insnhelper.c:3492
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(vm_call_cfunc_with_frame) /usr/src/ruby/vm_insnhelper.c:3518
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(vm_call_cfunc_other) /usr/src/ruby/vm_insnhelper.c:3544
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(vm_sendish+0xac) [0x7f1206b4d709] /usr/src/ruby/vm_insnhelper.c:5581
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(vm_exec_core) /usr/src/ruby/insns.def:834
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_vm_exec+0x179) [0x7f1206b53589] /usr/src/ruby/vm.c:2486
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_intern_const+0x0) [0x7f1206ab0d0f] /usr/src/ruby/ruby.c:1730
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(ruby_init_prelude) /usr/src/ruby/ruby.c:1731
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(ruby_opt_init) /usr/src/ruby/ruby.c:1791
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(ruby_opt_init+0x16) [0x7f1206ab132e] /usr/src/ruby/ruby.c:1749
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(load_file_internal) /usr/src/ruby/ruby.c:2599
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(rb_ensure+0x110) [0x7f120696e4f0] /usr/src/ruby/eval.c:1009
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(load_file+0x4b) [0x7f1206ab2d5b] /usr/src/ruby/ruby.c:2760
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(process_options) /usr/src/ruby/ruby.c:2296
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(ruby_process_options+0x145) [0x7f1206ab34a5] /usr/src/ruby/ruby.c:3014
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/lib/libruby.so.3.3(ruby_options+0xc9) [0x7f120696f5a9] /usr/src/ruby/eval.c:121
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/bin/ruby(rb_main+0x19) [0x55c71525a10a] ./main.c:39
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/usr/local/bin/ruby(main) ./main.c:58
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/lib/x86_64-linux-gnu/libc.so.6(__libc_start_call_main+0x7a) [0x7f12064d71ca] ../sysdeps/nptl/libc_start_call_main.h:58
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/lib/x86_64-linux-gnu/libc.so.6(call_init+0x0) [0x7f12064d7285] ../csu/libc-start.c:360
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main_impl) ../csu/libc-start.c:347
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main) (null):0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info][0x55c71525a151]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]-- Other runtime information -----------------------------------------------
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]* Loaded script: ruby
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]* Loaded features:
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    0 enumerator.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    1 thread.rb
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    2 fiber.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    3 rational.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    4 complex.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    5 ruby2_keywords.rb
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    6 /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/encdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    7 /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/trans/transdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    8 /usr/local/lib/ruby/3.3.0/x86_64-linux/rbconfig.rb
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]    9 /usr/local/lib/ruby/site_ruby/3.3.0/rubygems/compatibility.rb
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]   10 /usr/local/lib/ruby/site_ruby/3.3.0/rubygems/defaults.rb
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]   11 /usr/local/lib/ruby/site_ruby/3.3.0/rubygems/deprecate.rb
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]   12 /usr/local/lib/ruby/site_ruby/3.3.0/rubygems/errors.rb
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]* Process memory map:
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]55c715259000-55c71525a000 r--p 00000000 fe:00 5620                       /usr/local/bin/ruby
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]55c71525a000-55c71525b000 r-xp 00001000 fe:00 5620                       /usr/local/bin/ruby
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]55c71525b000-55c71525c000 r--p 00002000 fe:00 5620                       /usr/local/bin/ruby
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]55c71525c000-55c71525d000 r--p 00002000 fe:00 5620                       /usr/local/bin/ruby
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]55c71525d000-55c71525e000 rw-p 00003000 fe:00 5620                       /usr/local/bin/ruby
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]55c717151000-55c7176dd000 rw-p 00000000 00:00 0                          [heap]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1200775000-7f120094b000 r--s 00000000 fe:00 720                        /usr/lib/x86_64-linux-gnu/libc.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120094b000-7f1201d40000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1201d40000-7f1202f60000 r--s 00000000 fe:00 5833                       /usr/local/lib/libruby.so.3.3.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1202f60000-7f1202f70000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203080000-7f1203090000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203120000-7f1203130000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120316a000-7f12031a0000 r--s 00000000 fe:00 5620                       /usr/local/bin/ruby
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12031a0000-7f1203200000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120320f000-7f1203210000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203210000-7f12032b1000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12032b1000-7f12032b2000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12032b2000-7f1203353000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203353000-7f1203354000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203354000-7f12033f5000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12033f5000-7f12033f6000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12033f6000-7f1203497000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203497000-7f1203498000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203498000-7f1203539000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203539000-7f120353a000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120353a000-7f12035db000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12035db000-7f12035dc000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12035dc000-7f120367d000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120367d000-7f120367e000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120367e000-7f120371f000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120371f000-7f1203720000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203720000-7f12037c1000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12037c1000-7f12037c2000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12037c2000-7f1203863000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203863000-7f1203864000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203864000-7f1203905000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203905000-7f1203906000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203906000-7f12039a7000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12039a7000-7f12039a8000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12039a8000-7f1203a49000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203a49000-7f1203a4a000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203a4a000-7f1203aeb000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203aeb000-7f1203aec000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203aec000-7f1203b8d000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203b8d000-7f1203b8e000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203b8e000-7f1203c2f000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203c2f000-7f1203c30000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203c30000-7f1203cd1000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203cd1000-7f1203cd2000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203cd2000-7f1203d73000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203d73000-7f1203d74000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203d74000-7f1203e15000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203e15000-7f1203e16000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203e16000-7f1203eb7000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203eb7000-7f1203eb8000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203eb8000-7f1203f59000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203f59000-7f1203f5a000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203f5a000-7f1203ffb000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203ffb000-7f1203ffc000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1203ffc000-7f120409d000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120409d000-7f120409e000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120409e000-7f120413f000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120413f000-7f1204140000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1204140000-7f12041e1000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12041e1000-7f12041e2000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12041e2000-7f1204283000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1204283000-7f1204284000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1204284000-7f1204325000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1204325000-7f1204326000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1204326000-7f12043c7000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12043c7000-7f12043c8000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12043c8000-7f1204469000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1204469000-7f120446a000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120446a000-7f120450b000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120450b000-7f120450c000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120450c000-7f12045ad000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12045ad000-7f12045ae000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12045ae000-7f120464f000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120464f000-7f1204650000 ---p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1204650000-7f1204ea0000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1204eaf000-7f1206320000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206325000-7f1206326000 r--p 00000000 fe:00 7192                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/trans/transdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206326000-7f1206327000 r-xp 00001000 fe:00 7192                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/trans/transdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206327000-7f1206328000 r--p 00002000 fe:00 7192                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/trans/transdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206328000-7f1206329000 r--p 00002000 fe:00 7192                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/trans/transdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206329000-7f120632a000 rw-p 00003000 fe:00 7192                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/trans/transdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120632a000-7f120632b000 r--p 00000000 fe:00 7148                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/encdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120632b000-7f120632c000 r-xp 00001000 fe:00 7148                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/encdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120632c000-7f120632d000 r--p 00002000 fe:00 7148                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/encdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120632d000-7f120632e000 r--p 00002000 fe:00 7148                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/encdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120632e000-7f120632f000 rw-p 00003000 fe:00 7148                       /usr/local/lib/ruby/3.3.0/x86_64-linux/enc/encdb.so
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120632f000-7f1206430000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206430000-7f1206437000 r--s 00000000 fe:00 693                        /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206437000-7f120648e000 r--p 00000000 fe:00 337                        /usr/lib/locale/C.utf8/LC_CTYPE
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120648e000-7f1206490000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206490000-7f1206493000 r--p 00000000 fe:00 742                        /usr/lib/x86_64-linux-gnu/libgcc_s.so.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206493000-7f12064aa000 r-xp 00003000 fe:00 742                        /usr/lib/x86_64-linux-gnu/libgcc_s.so.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12064aa000-7f12064ae000 r--p 0001a000 fe:00 742                        /usr/lib/x86_64-linux-gnu/libgcc_s.so.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12064ae000-7f12064af000 r--p 0001d000 fe:00 742                        /usr/lib/x86_64-linux-gnu/libgcc_s.so.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12064af000-7f12064b0000 rw-p 0001e000 fe:00 742                        /usr/lib/x86_64-linux-gnu/libgcc_s.so.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12064b0000-7f12064d6000 r--p 00000000 fe:00 720                        /usr/lib/x86_64-linux-gnu/libc.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12064d6000-7f120662b000 r-xp 00026000 fe:00 720                        /usr/lib/x86_64-linux-gnu/libc.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120662b000-7f120667e000 r--p 0017b000 fe:00 720                        /usr/lib/x86_64-linux-gnu/libc.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120667e000-7f1206682000 r--p 001ce000 fe:00 720                        /usr/lib/x86_64-linux-gnu/libc.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206682000-7f1206684000 rw-p 001d2000 fe:00 720                        /usr/lib/x86_64-linux-gnu/libc.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206684000-7f1206693000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206693000-7f12066a3000 r--p 00000000 fe:00 759                        /usr/lib/x86_64-linux-gnu/libm.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12066a3000-7f1206716000 r-xp 00010000 fe:00 759                        /usr/lib/x86_64-linux-gnu/libm.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206716000-7f1206770000 r--p 00083000 fe:00 759                        /usr/lib/x86_64-linux-gnu/libm.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206770000-7f1206771000 r--p 000dc000 fe:00 759                        /usr/lib/x86_64-linux-gnu/libm.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206771000-7f1206772000 rw-p 000dd000 fe:00 759                        /usr/lib/x86_64-linux-gnu/libm.so.6
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206772000-7f1206774000 r--p 00000000 fe:00 729                        /usr/lib/x86_64-linux-gnu/libcrypt.so.1.1.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206774000-7f120678a000 r-xp 00002000 fe:00 729                        /usr/lib/x86_64-linux-gnu/libcrypt.so.1.1.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120678a000-7f12067a4000 r--p 00018000 fe:00 729                        /usr/lib/x86_64-linux-gnu/libcrypt.so.1.1.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12067a4000-7f12067a5000 r--p 00031000 fe:00 729                        /usr/lib/x86_64-linux-gnu/libcrypt.so.1.1.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12067a5000-7f12067a6000 rw-p 00032000 fe:00 729                        /usr/lib/x86_64-linux-gnu/libcrypt.so.1.1.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12067a6000-7f12067ae000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12067ae000-7f12067b9000 r--p 00000000 fe:00 746                        /usr/lib/x86_64-linux-gnu/libgmp.so.10.4.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f12067b9000-7f1206816000 r-xp 0000b000 fe:00 746                        /usr/lib/x86_64-linux-gnu/libgmp.so.10.4.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206816000-7f120682d000 r--p 00068000 fe:00 746                        /usr/lib/x86_64-linux-gnu/libgmp.so.10.4.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120682d000-7f120682e000 r--p 0007f000 fe:00 746                        /usr/lib/x86_64-linux-gnu/libgmp.so.10.4.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120682e000-7f120682f000 rw-p 00080000 fe:00 746                        /usr/lib/x86_64-linux-gnu/libgmp.so.10.4.1
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120682f000-7f1206832000 r--p 00000000 fe:00 819                        /usr/lib/x86_64-linux-gnu/libz.so.1.2.13
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206832000-7f1206845000 r-xp 00003000 fe:00 819                        /usr/lib/x86_64-linux-gnu/libz.so.1.2.13
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206845000-7f120684c000 r--p 00016000 fe:00 819                        /usr/lib/x86_64-linux-gnu/libz.so.1.2.13
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120684c000-7f120684d000 r--p 0001c000 fe:00 819                        /usr/lib/x86_64-linux-gnu/libz.so.1.2.13
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120684d000-7f120684e000 rw-p 0001d000 fe:00 819                        /usr/lib/x86_64-linux-gnu/libz.so.1.2.13
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206851000-7f120689b000 r--p 00000000 fe:00 5833                       /usr/local/lib/libruby.so.3.3.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f120689b000-7f1206c8f000 r-xp 0004a000 fe:00 5833                       /usr/local/lib/libruby.so.3.3.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206c8f000-7f1206e17000 r--p 0043e000 fe:00 5833                       /usr/local/lib/libruby.so.3.3.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206e17000-7f1206e2d000 r--p 005c5000 fe:00 5833                       /usr/local/lib/libruby.so.3.3.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206e2d000-7f1206e31000 rw-p 005db000 fe:00 5833                       /usr/local/lib/libruby.so.3.3.0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206e31000-7f1206e48000 rw-p 00000000 00:00 0
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206e48000-7f1206e49000 r--p 00000000 fe:00 702                        /usr/lib/x86_64-linux-gnu/ld-linux-x86-64.so.2
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206e49000-7f1206e6e000 r-xp 00001000 fe:00 702                        /usr/lib/x86_64-linux-gnu/ld-linux-x86-64.so.2
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206e6e000-7f1206e78000 r--p 00026000 fe:00 702                        /usr/lib/x86_64-linux-gnu/ld-linux-x86-64.so.2
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206e78000-7f1206e7a000 r--p 00030000 fe:00 702                        /usr/lib/x86_64-linux-gnu/ld-linux-x86-64.so.2
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7f1206e7a000-7f1206e7c000 rw-p 00032000 fe:00 702                        /usr/lib/x86_64-linux-gnu/ld-linux-x86-64.so.2
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7ffdcb703000-7ffdcbf02000 rw-p 00000000 00:00 0                          [stack]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7ffdcbf13000-7ffdcbf17000 r--p 00000000 00:00 0                          [vvar]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]7ffdcbf17000-7ffdcbf19000 r-xp 00000000 00:00 0                          [vdso]
2024-01-14T13:01:47Z app[e7842741b2ede8] bog [info]ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
2024-01-14T13:01:48Z app[e7842741b2ede8] bog [info] INFO Main child exited with signal (with signal 'SIGSEGV', core dumped? false)
2024-01-14T13:01:48Z app[e7842741b2ede8] bog [info] INFO Starting clean up.
2024-01-14T13:01:48Z app[e7842741b2ede8] bog [info] WARN hallpass exited, pid: 306, status: signal: 15 (SIGTERM)
2024-01-14T13:01:48Z app[e7842741b2ede8] bog [info]2024/01/14 13:01:48 listening on [fdaa:0:5b8f:a7b:273:31b9:ec96:2]:22 (DNS: [fdaa::3]:53)
2024-01-14T13:01:49Z app[e7842741b2ede8] bog [info][    2.277655] reboot: Restarting system
```

GDB backtrace

```
Thread 1 "ruby" received signal SIGSEGV, Segmentation fault.
redblack_new (right=0x0, left=0x0, value=0x7ffff602f3e8, key=49891, color=1 '\001') at shape.c:149
149     shape.c: No such file or directory.
(gdb) bt
#0  redblack_new (right=0x0, left=0x0, value=0x7ffff602f3e8, key=49891, color=1 '\001') at shape.c:149
#1  redblack_insert_aux (tree=<optimized out>, key=49891, value=value@entry=0x7ffff602f3e8) at shape.c:247
#2  0x00007ffff7c319df in redblack_insert (value=0x7ffff602f3e8, key=<optimized out>, tree=<optimized out>) at shape.c:287
#3  redblack_cache_ancestors (shape=0x7ffff602f3e8) at shape.c:434
#4  0x00007ffff7c319bd in redblack_cache_ancestors (shape=0x7ffff602f410) at shape.c:431
#5  redblack_cache_ancestors (shape=0x7ffff602f438) at shape.c:431
#6  0x00007ffff7c319bd in redblack_cache_ancestors (shape=0x7ffff602f460) at shape.c:431
#7  redblack_cache_ancestors (shape=0x7ffff602f488) at shape.c:431
#8  0x00007ffff7c319bd in redblack_cache_ancestors (shape=0x7ffff602f4b0) at shape.c:431
#9  redblack_cache_ancestors (shape=0x7ffff602f4d8) at shape.c:431
#10 0x00007ffff7c319bd in redblack_cache_ancestors (shape=0x7ffff602f500) at shape.c:431
#11 redblack_cache_ancestors (shape=0x7ffff602f528) at shape.c:431
#12 0x00007ffff7c319bd in redblack_cache_ancestors (shape=0x7ffff602f550) at shape.c:431
#13 redblack_cache_ancestors (shape=0x7ffff602f578) at shape.c:431
#14 0x00007ffff7c32908 in rb_shape_alloc_new_child (shape_type=SHAPE_IVAR, shape=0x7ffff602f550, id=49811) at shape.c:473
#15 get_next_shape_internal (new_variations_allowed=<optimized out>, variation_created=<synthetic pointer>, shape_type=SHAPE_IVAR, id=49811, shape=0x7ffff602f550) at shape.c:529
#16 rb_shape_get_next (shape=shape@entry=0x7ffff602f550, obj=obj@entry=140737320484760, id=id@entry=49811) at shape.c:721
#17 0x00007ffff7caea10 in general_ivar_set (too_complex_table_func=<optimized out>, transition_too_complex_func=<optimized out>, set_shape_func=<optimized out>, shape_resize_ivptr_func=<optimized out>, shape_ivptr_func=<optimized out>, data=0x0, val=140737290459360,
    id=49811, obj=140737320484760) at variable.c:1513
#18 rb_class_ivar_set (obj=obj@entry=140737320484760, id=id@entry=49811, val=val@entry=140737290459360) at variable.c:4236
#19 0x00007ffff7caebf3 in ivar_set (val=140737290459360, id=49811, obj=140737320484760) at variable.c:1844
#20 ivar_set (val=140737290459360, id=49811, obj=140737320484760) at variable.c:1831
#21 rb_ivar_set (obj=140737320484760, id=49811, val=140737290459360) at variable.c:1857
#22 0x00007ffff7ccaeaa in vm_exec_core (ec=0x55555555a0c0, ec@entry=0x55555555dac0) at /usr/src/ruby/vm_insnhelper.c:1639
#23 0x00007ffff7cd0589 in rb_vm_exec (ec=0x55555555dac0) at vm.c:2486
#24 0x00007ffff7cd1549 in rb_iseq_eval (iseq=iseq@entry=0x7ffff42a7370) at vm.c:2741
#25 0x00007ffff7b5358f in load_iseq_eval (fname=<optimized out>, ec=<optimized out>) at load.c:774
#26 require_internal (ec=ec@entry=0x55555555dac0, fname=<optimized out>, fname@entry=140737290398920, exception=exception@entry=1, warn=<optimized out>) at load.c:1281
#27 0x00007ffff7b54226 in rb_require_string_internal (resurrect=false, fname=140737290398920) at load.c:1380
#28 rb_require_string (fname=<optimized out>) at load.c:1373
#29 0x00007ffff7cb93b9 in vm_call_cfunc_with_frame_ (stack_bottom=<optimized out>, argv=<optimized out>, argc=<optimized out>, calling=<optimized out>, reg_cfp=<optimized out>, ec=<optimized out>) at /usr/src/ruby/vm_insnhelper.c:3490
#30 vm_call_cfunc_with_frame (calling=<optimized out>, reg_cfp=<optimized out>, ec=<optimized out>) at /usr/src/ruby/vm_insnhelper.c:3518
#31 vm_call_cfunc_other (ec=0x55555555dac0, reg_cfp=0x7ffff75abfa0, calling=<optimized out>) at /usr/src/ruby/vm_insnhelper.c:3544
#32 0x00007ffff7cca709 in vm_sendish (method_explorer=<optimized out>, block_handler=<optimized out>, cd=<optimized out>, reg_cfp=<optimized out>, ec=<optimized out>) at /usr/src/ruby/vm_callinfo.h:408
#33 vm_exec_core (ec=0x55555555a0c0, ec@entry=0x55555555dac0) at /usr/src/ruby/insns.def:834
#34 0x00007ffff7cd0589 in rb_vm_exec (ec=0x55555555dac0) at vm.c:2486
#35 0x00007ffff7c2dd0f in ruby_init_prelude () at ruby.c:1730
#36 ruby_opt_init (opt=opt@entry=0x7fffffffe680) at ruby.c:1791
#37 0x00007ffff7c2e32e in ruby_opt_init (opt=0x7fffffffe680) at ruby.c:1749
#38 load_file_internal (argp_v=argp_v@entry=140737488343872) at ruby.c:2599
#39 0x00007ffff7aeb4f0 in rb_ensure (b_proc=b_proc@entry=0x7ffff7c2deb0 <load_file_internal>, data1=data1@entry=140737488343872, e_proc=e_proc@entry=0x7ffff7c2a390 <restore_load_file>, data2=data2@entry=140737488343872) at eval.c:1009
#40 0x00007ffff7c2fd5b in load_file (opt=0x7fffffffe680, script=1, f=140737320554760, fname=<optimized out>, parser=140737290695800) at ruby.c:2760
#41 process_options (argc=0, argc@entry=1, argv=0x7fffffffe970, argv@entry=0x7fffffffe968, opt=opt@entry=0x7fffffffe680) at ruby.c:2296
#42 0x00007ffff7c304a5 in ruby_process_options (argc=argc@entry=1, argv=argv@entry=0x7fffffffe968) at ruby.c:229
#43 0x00007ffff7aec5a9 in ruby_options (argc=argc@entry=1, argv=argv@entry=0x7fffffffe968) at eval.c:121
#44 0x000055555555510a in rb_main (argv=0x7fffffffe968, argc=1) at ./main.c:39
#45 main (argc=<optimized out>, argv=<optimized out>) at ./main.c:58
```
