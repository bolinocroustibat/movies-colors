# Movies Color Palettes

Generate color palettes from movies files (`.avi`, `.mkv` and `.mp4` files).

Place the movies files on a Google Drive, connect it to the notebook, as instructed in the notebook.

## Related Projects

This repository works in conjunction with [movies-palettes-frontend](https://github.com/bolinocroustibat/movies-palettes-frontend), which provides a web interface to display the generated color palettes.

## Database Setup

The application requires a SQLite database. You must create the database with the following schema:

```sql
CREATE TABLE "movies" (
	"id" INTEGER PRIMARY KEY AUTOINCREMENT,
	"title" VARCHAR NOT NULL UNIQUE,
	"type" VARCHAR,
	"status" VARCHAR,
	"path" VARCHAR,
	"director" VARCHAR,
	"year" VARCHAR,
	"added" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE "palettes" (
	"id" varchar NOT NULL,
	"movie_id" int NOT NULL,
	"clusters_nb" int NOT NULL,
	"calculation_date" DATETIME DEFAULT CURRENT_TIMESTAMP,
	"calculation_duration_seconds" REAL,
	"runtime" varchar,
	"frame_skip" int,
	"resize_width" int,
	"resize_height" int,
	"batch_size" int,
	"colors" text NOT NULL,
	"clustering_method" varchar NOT NULL,
	"is_black_and_white" BOOLEAN DEFAULT FALSE,
	"length" int,
	PRIMARY KEY (id)
);
```
