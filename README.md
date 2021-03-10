# ChessProject - Java Solution Notes

### Modifications to `Pawn` Class
* `Pawn` class has been subclassed from a new abstract `ChessPiece` base class, to facilitate future addition of other piece types.
*  Reference to `ChessBoard` from pawn/piece class has been removed to avoid circular dependency between these. (If knowledge of the board is necessary for a piece in future for some reason, could use some kind of observer/callback interface to avoid circular dependency)
* Helper method added to base class to translate pairs of absolute co-ords to left/forward relative moves, allowing identical checking of moves for black and white pieces.

### Modifications to `ChessBoard` Class
*  An overloaded `Add` method has been implemented, making use of piece type codes and the new `ChessPieceFactory` to allow addition of pieces to the board without caller creating the piece first. This is intended as a convenience for callers such as UIs or setting up initial board state (e.g. to recreate famous games as per spec).
*  `Move` method has been added, which takes player colour and current and new board co-ordinates, and forwards the move to the appropriate piece as either a move or capture depending on the current board state.
`toString` method has been added to render a board as an 8x8 grid, with character codes for pieces. This aids visualization for debugging and checking of board states for testing.
*  These three methods are intended as the start of an API for a caller, allowing boards to be set up, played, and rendered, at least in some fashion, for pawns. Future additions could include parsing board set up from a text representation and parsing a list of moves in chess algebraic notation.
*  The constants indicating board height and width have been changed to 8 for more idiomatic Java usage of array allocation and indexing (0 <= x < n)
*  The element type of the board is now `ChessPiece` rather than `Pawn`

### Modifications to tests and existing code
  * These are detailed in the code
