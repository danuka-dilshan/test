import { useState } from "react";

function App() {
  const MAX_CHARACTERS = 200;

  const [text, setText] = useState("");

  // Character count
  const characterCount = text.length;

  // Word count
  const wordCount =
    text.trim() === "" ? 0 : text.trim().split(/\s+/).length;

  // Sentence count
  const sentenceCount =
    text.trim() === ""
      ? 0
      : text
          .trim()
          .split(/[.!?]+/)
          .filter((sentence) => sentence.trim() !== "").length;

  // Remaining characters
  const remainingCharacters = MAX_CHARACTERS - characterCount;

  // Handle text change
  const handleChange = (e) => {
    const newText = e.target.value;

    if (newText.length <= MAX_CHARACTERS) {
      setText(newText);
    }
  };

  // Clear text
  const handleClear = () => {
    setText("");
  };

  return (
    <div>
      <h1>Character Counter</h1>

      <textarea
        value={text}
        onChange={handleChange}
        placeholder="Type your text here..."
        rows="10"
        cols="50"
      />

      <div>
        <p>Character Count: {characterCount}</p>

        <p>Word Count: {wordCount}</p>

        <p>Sentence Count: {sentenceCount}</p>

        <p>Remaining Characters: {remainingCharacters}</p>

        <p>
          Maximum Characters: {MAX_CHARACTERS}
        </p>
      </div>

      <button onClick={handleClear}>
        Clear
      </button>
    </div>
  );
}

export default App;

