#lang eopl
(require rackunit)

(require "lab_sets_relations.rkt")

;; union tests
(check-equal? (union '(1 2 3) '(4 5 6)) '(1 2 3 4 5 6))
(check-equal? (union '(c b f d) '(b c a)) '(a b c d f))
(check-equal? (union '("abc") '()) '("abc"))
(check-equal? (union '((z) (x y)) '((y x) (z))) '((z) (x y) (y x)))

;; intersection tests
(check-equal? (intersection '(1 2 3 4) '(2 4 5)) '(2 4))
(check-equal? (intersection '(s a n d e p) '(b h a t)) '(a))
(check-equal? (intersection '("abc") '("ab")) '())
(check-equal? (intersection '((x y) (z)) '((x y) (y x))) '((x y)))

;; disjoint tests
(check-equal? (disjoint? '(1 2 3) '()) #t)
(check-equal? (disjoint? '(a b c) '(b)) #f)
(check-equal? (disjoint? '((x z)) '((x y) (z))) #t)

;; subset tests
(check-equal? (subset? '() '()) #t)
(check-equal? (subset? '(1 2 3) '(4 1 3 5 2)) #t)
(check-equal? (subset? '(b a c) '(d f e a g)) #f)
(check-equal? (subset? '(1 3 2) '(3 2 1)) #t)

;; Import the functions to test
(require "set-functions.rkt")
(require "relation-functions.rkt")


;; Test set-equal?
(check-equal? (set-equal? '() '()) #t)
(check-equal? (set-equal? '(a b c) '(a b c)) #t)
(check-equal? (set-equal? '(1 2 3 4) '(4 3 1 2)) #t)
(check-equal? (set-equal? '("c" "b" "d" "a") '("a" "c" "b")) #f)

;; Test difference
(check-equal? (difference '(1 2 3) '(2 3 4)) '(1))
(check-equal? (difference '(x y z) '(y x z)) '())
(check-equal? (difference '(1 2 3) '(4 5 6)) '(1 2 3))
(check-equal? (difference '() '("x" "y")) '())
(check-equal? (difference '("xyz") '()) '("xyz"))

;; Test sym-diff
(check-equal? (sym-diff '(1 2 3) '(3 4 5)) '(1 2 4 5))
(check-equal? (sym-diff '(a b c) '(d e f)) '(a b c d e f))
(check-equal? (sym-diff '(1 2 3) '(1 2 3)) '())
(check-equal? (sym-diff '(1 2) '(1 2 3 4)) '(3 4))
(check-equal? (sym-diff '(1) '()) '(1))

;; Test id
(check-equal? (id 1) '((1 1)))
(check-equal? (id 2) '((1 1) (2 2)))
(check-equal? (id 5) '((1 1) (2 2) (3 3) (4 4) (5 5)))

;; Test reflexive?
(check-equal? (reflexive? 3 '()) #f)
(check-equal? (reflexive? 2 '((3 3) (1 1) (2 2))) #t)
(check-equal? (reflexive? 3 '((2 3) (1 1) (3 3) (3 4) (2 2))) #t)
(check-equal? (reflexive? 4 '((1 1) (2 2) (3 3))) #f)
(check-equal? (reflexive? 1 '((1 4) (2 3) (3 1) (3 3) (4 4))) #f)
(check-equal? (reflexive? 2 '((4 3) (2 2) (1 3) (1 1))) #t)

;; Test reflexive-closure
(check-equal? (reflexive-closure 3 '()) '((1 1) (2 2) (3 3)))
(check-equal? (reflexive-closure 3 '((3 2))))