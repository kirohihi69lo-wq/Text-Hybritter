# Text-Hybritter
A small text workshop that designs your output.

🌸 What is this?

This project is a **hybrid text engine** that merges  
styled rendering with a lightweight, stream-oriented pipeline.  
It’s built to handle **console layout, styled sequences, buffering, and metrics**  
in a consistent and extensible way.

Think of it as a **text craftsman**:  
laying out words with care, remembering their flow,  
and quietly measuring how well it all performed.

---

✨ Key Components

- **StyleMap** – A simple mapping of style names to ANSI codes.  
  Add your own or use the defaults (`bold`, `error`, `success`…).

- **Segment / StyledText** – Immutable text units with style and attributes.  
  Can be concatenated, sliced, normalized, or searched.

- **ConsoleRenderer** – Prints text gracefully with wrapping, alignment,  
  cache, and plain fallback when needed.

- **TextBuffer** – A buffered writer with history.  
  Searchable, undo-able, and snapshot-able — a small diary of your console.

- **SonicBuffer** – Binary ring buffer using memory mapping.  
  Handles fast I/O and back-pressure experiments.

- **DeltaGate** – A codec dispatcher (UTF-8, JSON, CSV, …).  
  Easy to extend when new formats are needed.

- **SonicMeter** – Records performance metrics like latency, QPS, memory use.  
  A lightweight stopwatch for your pipeline.

- **Pipeline** – Connects everything together.  
  Render → Buffer → Encode → Write → Measure, in one flow.

---

🪄 Why use it?

- **Readable output** with styled or plain fallback.  
- **Searchable buffer** with undo and snapshots.  
- **Built-in metrics** for quick performance insights.  
- **Composable blocks** that can be combined freely.

---

🌱 Example

from hybrid_layout import StyleMap, StyledText, Pipeline

stylemap = StyleMap()
txt = StyledText.from_pairs([
    ("Hello ", "success"),
    ("World", "error")
])

pipe = Pipeline()
pipe.run(txt)

print("Snapshot:", pipe.buffer.snapshot())
print("Rolling:", pipe.meter.rolling())

🧩 About the Extras

You may notice mathematical routines (FFT, summation, GEMM, etc.) in the source.
They are included mainly as performance benchmarks and playground code.
The layout engine is the true core.

📜 License

MIT / HIROKI License
Free to use, modify, and share.
Credit is always appreciated 🌷
