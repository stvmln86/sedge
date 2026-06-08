# Sedge

**Sedge** is a command-line note-taking application, written in Go 1.26 by Stephen Malone.


```json
// alpha/b4a63e72c1a1857f36f74814756b744276724579a8ae4b4145bae3d1eed811a5.json
{
  "base": "a0d6039111a7d805b0b845ca44ac3b3efc294bb0a21cc75cf93b176d29a8a8bb",
  "body": "Alpha two.",
  "time": "1970-01-01 01:00:00 UTC",
}

// alpha/a0d6039111a7d805b0b845ca44ac3b3efc294bb0a21cc75cf93b176d29a8a8bb.json
{
  "body": "Alpha one.",
  "time": "1970-01-01 00:00:00 UTC"
}
```

```
$ sedge echo alpha
Alpha two.

$ sedge hist alpha
[0] 1970-01-01 00:00:00:
  Alpha one.

[1] 1970-01-01 01:00:00
  Alpha two.
```

```go
type Page struct {
	Base string
	Body string
	Time time.Time
}

func (p *Page) Hash() string

type Note struct {
	Dire string
	Mode os.FileMode
}

func (n *Note) List()   ([]*Page, error)
func (n *Note) Latest() (*Page, error)
func (n *Note) Name()   string

type Book struct {
	Base string
	Mode os.FileMode
}

func (b *Book) Get(name string) (*Note, error)
```
