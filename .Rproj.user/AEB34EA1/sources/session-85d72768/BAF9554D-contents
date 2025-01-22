#' Complete list of palettes
#'
#' Use \code{\link{gdc_palettes}} to construct palettes of desired length.
#'
#' @export
gdc_palettes <- list(
  PiazzaDItalia = c("#d8ba6c", "#897758", "#a2a773", "#a74834", "#8698a4", "#5b6871"),
  LeMuseInquietanti = c("#f5a70a", "#ea5923", "#543a2a", "#b17046", "#014841", "#efbd81"),
  SoleSulCavalletto1972 = c("#913520", "#3f441e", "#1b1a23", "#697784", "#f9af24", "#b2926f"),
  PiazzaDItalia1939 = c("#283a4c", "#f1ebdd", "#4d392e", "#a96540", "#5f2c1b", "#a97d2b"),
  ArrivoDelTrasloco1965 = c("#e7e0da", "#d29b36", "#994f1f", "#4e573d", "#5279a6", "#354141"),
  Zissou1Continuous = c("#3A9AB2", "#6FB2C1", "#91BAB6", "#A5C2A3", "#BDC881", "#DCCB4E", "#E3B710", "#E79805", "#EC7A05", "#EF5703", "#F11B00")
)

#' A Giorgio De Chirico color palette generator
#'
#' These are a handful of color palettes from Giorgio De Chirico paintings.
#'
#' @param n Number of colors desired. Unfortunately most palettes now only
#'   have 4 or 5 colors. But hopefully we'll add more palettes soon.
#' @param name Name of desired palette. Choices are:
#'   \code{PiazzaDItalia}, \code{LeMuseInquietanti}, \code{SoleSulCavalletto1972},
#'   \code{PiazzaDItalia1939}, \code{ArrivoDelTrasloco1965}
#' @param type Either "continuous" or "discrete". Use continuous if you want
#'   to automatically interpolate between colours.
#'   @importFrom graphics rgb rect par image text
#' @return A vector of colours.
#' @export
#' @keywords colors
#' @examples
#' gdc_palette("PiazzaDItalia")
#' gdc_palette("LeMuseInquietanti")
#' gdc_palette("SoleSulCavalletto1972")
#' gdc_palette("SoleSulCavalletto1972", 3)
#'
#' # If you need more colours than normally found in a palette, you
#' # can use a continuous palette to interpolate between existing
#' # colours
#' pal <- gdc_palette(21, name = "PiazzaDItalia", type = "continuous")
#' image(volcano, col = pal)
gdc_palette <- function(name, n, type = c("discrete", "continuous")) {
  type <- match.arg(type)

  pal <- gdc_palettes[[name]]
  if (type == "continuous" && name == "PiazzaDItalia") {
    pal <- gdc_palettes[["Zissou1Continuous"]]
  }

  if (is.null(pal))
    stop("Palette not found.")

  if (missing(n)) {
    n <- length(pal)
  }

  if (type == "discrete" && n > length(pal)) {
    stop("Number of requested colors greater than what palette can offer")
  }

  out <- switch(type,
                continuous = grDevices::colorRampPalette(pal)(n),
                discrete = pal[1:n]
  )
  structure(out, class = "palette", name = name)
}

#' @export
#' @importFrom graphics rect par image text
#' @importFrom grDevices rgb
print.palette <- function(x, ...) {
  n <- length(x)
  old <- par(mar = c(0.5, 0.5, 0.5, 0.5))
  on.exit(par(old))

  image(1:n, 1, as.matrix(1:n), col = x,
        ylab = "", xaxt = "n", yaxt = "n", bty = "n")

  rect(0, 0.9, n + 1, 1.1, col = rgb(1, 1, 1, 0.8), border = NA)
  text((n + 1) / 2, 1, labels = attr(x, "name"), cex = 1, family = "serif")
}
