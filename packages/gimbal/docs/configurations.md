# Gimbal Configurations

Available configurations for `config` section of your gimbal config file.

The configuration will be splited by audit types:

- [size](#size)
- [heap-snapshot](#heap-snapshot)
- [lighthouse](#lighthouse)

## size

Sets thresholds for given paths.

- Type: Path[] `Path { path: directoryPath, size: thresholdSize }`

Example:

```yaml
configs:
  size:
    - path: ./build/precache-*.js
      maxSize: 10 KB
    - path: ./build/static/js/[0-9]*.chunk.js
      maxSize: 1 MB
    - path: ./build/static/js/*.chunk.js
      maxSize: 1 MB
    - path: ./build/static/js/runtime*.js
      maxSize: 10 KB
    - path: ./build/index.html
      maxSize: 10 KB
    - path: ./build/favicon.ico
      maxSize: 10 KB
    - path: ./build/
      maxSize: 18 MB
```

## heap-snapshot

Heap snapshot threshold parameters configurations. All minimum default configurations and values aplied should look like:

```yaml
configs:
  heap-snapshot:
    threshold:
      Documents: 5
      Frames: 2
      LayoutCount: 5
      Nodes: 75
      RecalcStyleCount: 6
```

The complete configuration should look like:

```yaml
configs:
  heap-snapshot:
    threshold:
      Documents: 5
      Frames: 2
      JSHeapTotalSize: 200000
      JSHeapUsedSize: 100000
      LayoutCount: 5
      Nodes: 75
      RecalcStyleCount: 4
```

#### Documents

Number of documents in the page.

- Type: number
- Default value: 5

```yaml
configs:
  heap-snapshot:
    threshold:
      Documents: 5
```

#### Frames

Number of frames in the page.

- Type: number
- Default value: 2

```yaml
configs:
  heap-snapshot:
    threshold:
      Frames: 2
```

#### LayoutCount

Total number of full or partial page layout.

- Type: number
- Default value: 5

```yaml
configs:
  heap-snapshot:
    threshold:
      LayoutCount: 5
```

#### Nodes

Number of DOM nodes in the page.

- Type: number
- Default value: 75

```yaml
configs:
  heap-snapshot:
    threshold:
      Nodes: 75
```

#### RecalcStyleCount

Total number of page style recalculations.

- Type: number
- Default value: 6

Example:

```yaml
configs:
  heap-snapshot:
    threshold:
      RecalcStyleCount: 6
```

#### JSHeapTotalSize

Total JavaScript heap size.

- Type: number
- Default value: none

Example:

```yaml
configs:
  heap-snapshot:
    threshold:
      JSHeapTotalSize: 200000
```

#### JSHeapUsedSize

Used JavaScript heap size.

- Type: number
- Default value: none

Example:

```yaml
configs:
  heap-snapshot:
    threshold:
      JSHeapUsedSize: 100000
```


## lighthouse

Google lighthouse threshold parameters configurations. All minimum default configurations and values aplied should look like:

```yaml
configs:
  lighthouse:
    skipAudits:
      - uses-http2
      - redirects-http
      - uses-long-cache-ttl
    threshold:
      accessibility: 75
      "best-practices": 95
      performance: 50
      pwa: 52
      seo: 90
```

extends: 'lighthouse:default',
  settings: {
    skipAudits: ['uses-http2', 'redirects-http', 'uses-long-cache-ttl'],
  },
  threshold: {
    accessibility: 75,
    'best-practices': 95,
    performance: 50,
    pwa: 50,
    seo: 90,
  },

The complete configuration should look like:

```yaml
configs:
  lighthouse:
    skipAudits:
      - uses-http2
      - redirects-http
      - uses-long-cache-ttl
      - uses-text-compression
    outputHtml: artifacts/lighthouse.html
    threshold:
      accessibility: 90
      "best-practices": 92
      performance: 64
      pwa: 52
      seo: 100
```

#### skipAudits

Excludes the specified audits from the final report.

- Type: string[]
- Default value: [uses-http2, redirects-http, uses-long-cache-ttl]

Example:

```yaml
configs:
  lighthouse:
    skipAudits:
      - uses-http2
      - redirects-http
      - uses-long-cache-ttl
      - uses-text-compression
```
