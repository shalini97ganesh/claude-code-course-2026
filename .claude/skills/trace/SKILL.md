---
name: trace
description: Trace a DevLens tool call end-to-end through the codebase.
---

# /trace

Trace a tool call through DevLens.

Argument:
$ARGUMENTS = tool name

## Instructions

1. Search for the tool definition in tools.js.
2. Record the file name and line number.
3. Identify where the tool request is sent.
4. Identify how the response is processed.
5. Identify any API handlers involved.
6. Explain the full request/response lifecycle.

## Output Format

### Tool

<tool name>

### Definition

File:
Line:

### Request Flow

1.
2.
3.

### Response Flow

1.
2.
3.

### Summary

One paragraph explaining how the tool use cycle works.

## Example

Input:

/trace read_file

Output:

### Tool

read_file

### Definition

File: tools.js
Line: 120

### Request Flow

1. User requests file contents.
2. Claude selects read_file.
3. Request sent through API layer.

### Response Flow

1. Tool executes.
2. Result returned.
3. Claude receives and explains result.

### Summary

The read_file tool begins in tools.js and flows through the API before returning a response to Claude.