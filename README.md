# ElixirUpyun

[![travis-status](https://travis-ci.org/qhwa/elixir-upyun.svg?branch=master)](https://travis-ci.org/qhwa/elixir-upyun)
[![inch_doc_status](http://inch-ci.org/github/qhwa/elixir-upyun.svg?branch=master)](http://inch-ci.org/github/qhwa/elixir-upyun/suggestions)

Unofficial Upyun client for Elixir.

warning: This is an unofficial and under development SDK. APIs may change frequently. Do NOT use it in your production.

[online documents](https://hexdocs.pm/hlj_upyun/Upyun.html)

## Installation

The package can be installed as:

  1. Add `upyun` to your list of dependencies in `mix.exs`:

      ```elixir
      def deps do
        [{:hlj_upyun, "~> 0.1"}]
      end
      ```

  2. Ensure `upyun` is started before your application:

      ```elixir
      def application do
        [applications: [:upyun]]
      end
      ```

## Usage
Example:

```elixir
policy = %Upyun{ operator: "USER_NAME", password: "PASSWORD", bucket: "BUCKET" }

# upload a file
policy |> Upyun.upload(local_file_path, "/path/to/remote/file")
#=> :ok

# get file info
policy |> Upyun.info("/path/to/remote/file")

# list entries
policy |> Upyun.list("/")
#=> [{:file, 150, ...}, {:dir, 0, ...}, ...]

# put content to bucket, stores it as a file
policy |> Upyun.put(
  "THIS IS THE CONTENT OF THE FILE",
  "/path/to/remote/file"
)

# get content of the remote file
policy |> Upyun.get("/path/to/remote/file")
#=> "THIS IS THE CONTENT OF THE FILE"

# upload a dir recursively
policy |> Upyun.upload_dir("/path/to/local/dir", "/path/to/remote/dir")

# delete an object of remote
policy |> Upyun.delete("/path/to/remote/object")
```

## License
MIT


Feel free to [fork](https://github.com/qhwa/elixir-upyun) or submit [issues](https://github.com/qhwa/elixir-upyun/issues).
