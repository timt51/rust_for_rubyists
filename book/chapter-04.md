Testing
=======

Rubyists love testing, so before we go any farther, let's talk about
testing. In Rust, there is a unit testing framework built in, and it's
pretty simple. Let's write some very simple code and tests to exercise
it.

In Rust, you annotate test methods like such:

~~~ {.rust}
    #[test]
    fn this_tests_code() {
        // SOMETHING HERE
    }
~~~

You'll note that tests take no arguments and return nothing. If the
function runs, the test passes, and if it errors in some way, the test
fails. Let's give it a shot: Open up `testing.rs` and put this in it:

~~~ {.rust}
    #[test]
    fn this_tests_code() {
        println("")
    }
~~~

Then, use `rustc` with a special flag:

    $ rustc --test testing.rs

This tells `rustc` to compile your tests, and replaces the `main` function
with a test runner. Try it out:

    $ ./testing

You should get some output that looks like this:

    running 1 test

    test this_tests_code ... ok

    result: ok. 1 passed; 0 failed; 0 ignored

Bam! Now let's make it fail:

~~~ {.rust}
    #[test]
    fn this_tests_code() {
        fail!("Fail!");
    }
~~~

Recompile, and the output should be:

    $ ./testing

    running 1 test
    rust: task failed at 'Fail!', testing.rs:3
    test this_tests_code ... FAILED

    failures:
        this_tests_code

    result: FAILED. 0 passed; 1 failed; 0 ignored

    rust: task failed at 'Some tests failed', /build/src/rust-0.6/src/libstd/test.rs:104
    rust: domain main @0x1ca49c0 root task failed

You can see it gives us the message, the file name, and the line number.
Great.

Super simple. That's all you need to know to get started. Next up: FizzBuzz.
