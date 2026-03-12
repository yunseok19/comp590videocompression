# COMP590 Assignment 1 — Video Compression

## What I did

The baseline encodes each pixel as a temporal difference (current frame minus prior frame) using a single arithmetic coding model for every pixel.

My improvement: instead of one model, I use 8 models based on how much local activity surrounds each pixel in the prior frame. Smooth regions (sky, walls) get a different model than busy regions (edges, faces) because their difference distributions look completely different. Keeping them separate lets the arithmetic coder learn each one better.

Context is computed as: activity = |left - right| + |above - below|

using the 4 cardinal neighbours in the prior frame, then bucketed into 8 levels. Since the decoder has the same prior frame, no extra information needs to be transmitted.
