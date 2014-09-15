# Example ruby class spec

After following the path, you should have a spec like below, that runs when you `rake`:

**Example specification:**
``` ruby
require "minitest/autorun"
require "minitest/spec"
require "welcome"

describe Welcome do
  it "has a message" do
    hello = Welcome.new
    hello.message.must_match "Welcome"
  end
end
```
