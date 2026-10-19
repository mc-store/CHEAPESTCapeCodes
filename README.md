(globalThis.TURBOPACK || (globalThis.TURBOPACK = [])).push(["object" == typeof document ? document.currentScript : void 0, 974568, e => {
    "use strict";
    var t = e.i(939299)
      , r = e.i(37428)
      , a = e.i(491886);
    e.s(["HydrationBoundary", 0, ({children: e, options: s={}, state: n, queryClient: i}) => {
        let l = (0,
        t.useQueryClient)(i)
          , o = r.useRef(s);
        r.useEffect( () => {
            o.current = s
        }
        );
        let c = r.useMemo( () => {
            if (n) {
                if ("object" != typeof n)
                    return;
                let e = l.getQueryCache()
                  , t = n.queries || []
                  , r = []
                  , s = [];
                for (let a of t) {
                    let t = e.get(a.queryHash);
                    t ? (a.state.dataUpdatedAt > t.state.dataUpdatedAt || a.promise && "pending" !== t.state.status && "fetching" !== t.state.fetchStatus && void 0 !== a.dehydratedAt && a.dehydratedAt > t.state.dataUpdatedAt) && s.push(a) : r.push(a)
                }
                if (r.length > 0 && (0,
                a.hydrate)(l, {
                    queries: r
                }, o.current),
                s.length > 0)
                    return s
            }
        }
        , [l, n]);
        return r.useEffect( () => {
            c && (0,
            a.hydrate)(l, {
                queries: c
            }, o.current)
        }
        , [l, c]),
        e
    }
    ])
}
, 590368, (e, t, r) => {
    Object.defineProperty(r, "__esModule", {
        value: !0
    });
    var a = e.r(37428)
      , s = a && "object" == typeof a && "default" in a ? a : {
        default: a
    };
    !function(e) {
        if (!e || "u" < typeof window)
            return;
        let t = document.createElement("style");
        t.setAttribute("type", "text/css"),
        t.innerHTML = e,
        document.head.appendChild(t)
    }('.rfm-marquee-container {\n  overflow-x: hidden;\n  display: flex;\n  flex-direction: row;\n  position: relative;\n  width: var(--width);\n  transform: var(--transform);\n}\n.rfm-marquee-container:hover div {\n  animation-play-state: var(--pause-on-hover);\n}\n.rfm-marquee-container:active div {\n  animation-play-state: var(--pause-on-click);\n}\n\n.rfm-overlay {\n  position: absolute;\n  width: 100%;\n  height: 100%;\n}\n.rfm-overlay::before, .rfm-overlay::after {\n  background: linear-gradient(to right, var(--gradient-color), rgba(255, 255, 255, 0));\n  content: "";\n  height: 100%;\n  position: absolute;\n  width: var(--gradient-width);\n  z-index: 2;\n  pointer-events: none;\n  touch-action: none;\n}\n.rfm-overlay::after {\n  right: 0;\n  top: 0;\n  transform: rotateZ(180deg);\n}\n.rfm-overlay::before {\n  left: 0;\n  top: 0;\n}\n\n.rfm-marquee {\n  flex: 0 0 auto;\n  min-width: var(--min-width);\n  z-index: 1;\n  display: flex;\n  flex-direction: row;\n  align-items: center;\n  animation: scroll var(--duration) linear var(--delay) var(--iteration-count);\n  animation-play-state: var(--play);\n  animation-delay: var(--delay);\n  animation-direction: var(--direction);\n}\n@keyframes scroll {\n  0% {\n    transform: translateX(0%);\n  }\n  100% {\n    transform: translateX(-100%);\n  }\n}\n\n.rfm-initial-child-container {\n  flex: 0 0 auto;\n  display: flex;\n  min-width: auto;\n  flex-direction: row;\n  align-items: center;\n}\n\n.rfm-child {\n  transform: var(--transform);\n}'),
    r.default = a.forwardRef(function({style: e={}, className: t="", autoFill: r=!1, play: n=!0, pauseOnHover: i=!1, pauseOnClick: l=!1, direction: o="left", speed: c=50, delay: d=0, loop: u=0, gradient: m=!1, gradientColor: h="white", gradientWidth: x=200, onFinish: p, onCycleComplete: f, onMount: v, children: g}, b) {
        let[y,w] = a.useState(0)
          , [j,N] = a.useState(0)
          , [C,k] = a.useState(1)
          , [P,E] = a.useState(!1)
          , S = a.useRef(null)
          , _ = b || S
          , R = a.useRef(null)
          , A = a.useCallback( () => {
            if (R.current && _.current) {
                let e = _.current.getBoundingClientRect()
                  , t = R.current.getBoundingClientRect()
                  , a = e.width
                  , s = t.width;
                ("up" === o || "down" === o) && (a = e.height,
                s = t.height),
                r && a && s ? k(s < a ? Math.ceil(a / s) : 1) : k(1),
                w(a),
                N(s)
            }
        }
        , [r, _, o]);
        a.useEffect( () => {
            if (P && (A(),
            R.current && _.current)) {
                let e = new ResizeObserver( () => A());
                return e.observe(_.current),
                e.observe(R.current),
                () => {
                    e && e.disconnect()
                }
            }
        }
        , [A, _, P]),
        a.useEffect( () => {
            A()
        }
        , [A, g]),
        a.useEffect( () => {
            E(!0)
        }
        , []),
        a.useEffect( () => {
            "function" == typeof v && v()
        }
        , []);
        let T = a.useMemo( () => r ? j * C / c : j < y ? y / c : j / c, [r, y, j, C, c])
          , M = a.useMemo( () => Object.assign(Object.assign({}, e), {
            "--pause-on-hover": !n || i ? "paused" : "running",
            "--pause-on-click": !n || i && !l || l ? "paused" : "running",
            "--width": "up" === o || "down" === o ? "100vh" : "100%",
            "--transform": "up" === o ? "rotate(-90deg)" : "down" === o ? "rotate(90deg)" : "none"
        }), [e, n, i, l, o])
          , $ = a.useMemo( () => ({
            "--gradient-color": h,
            "--gradient-width": "number" == typeof x ? `${x}px` : x
        }), [h, x])
          , O = a.useMemo( () => ({
            "--play": n ? "running" : "paused",
            "--direction": "left" === o ? "normal" : "reverse",
            "--duration": `${T}s`,
            "--delay": `${d}s`,
            "--iteration-count": u ? `${u}` : "infinite",
            "--min-width": r ? "auto" : "100%"
        }), [n, o, T, d, u, r])
          , L = a.useMemo( () => ({
            "--transform": "up" === o ? "rotate(90deg)" : "down" === o ? "rotate(-90deg)" : "none"
        }), [o])
          , I = a.useCallback(e => [...Array(Number.isFinite(e) && e >= 0 ? e : 0)].map( (e, t) => s.default.createElement(a.Fragment, {
            key: t
        }, a.Children.map(g, e => s.default.createElement("div", {
            style: L,
            className: "rfm-child"
        }, e)))), [L, g]);
        return P ? s.default.createElement("div", {
            ref: _,
            style: M,
            className: "rfm-marquee-container " + t
        }, m && s.default.createElement("div", {
            style: $,
            className: "rfm-overlay"
        }), s.default.createElement("div", {
            className: "rfm-marquee",
            style: O,
            onAnimationIteration: f,
            onAnimationEnd: p
        }, s.default.createElement("div", {
            className: "rfm-initial-child-container",
            ref: R
        }, a.Children.map(g, e => s.default.createElement("div", {
            style: L,
            className: "rfm-child"
        }, e))), I(C - 1)), s.default.createElement("div", {
            className: "rfm-marquee",
            style: O
        }, I(C))) : null
    })
}
, 412753, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(781375)
      , a = e.i(344873)
      , s = e.i(610936);
    e.s(["DisplayPrice", 0, function({usdAmount: e, className: n, forceUsd: i=!1}) {
        let {currency: l, formatDisplayPrice: o} = (0,
        r.useCurrency)()
          , c = i ? (0,
        a.formatPrice)(e) : o(e);
        return (0,
        t.jsx)(s.NoTranslate, {
            className: n,
            children: c
        }, `${l}-${c}`)
    }
    ])
}
, 448358, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(340675)
      , a = e.i(585653)
      , s = e.i(936976)
      , n = e.i(610936);
    let i = [{
        label: "Home",
        href: "/"
    }, {
        label: "Shop",
        href: "/shop"
    }, {
        label: "Endorsements",
        href: "/videos"
    }, {
        label: "Reviews",
        href: "/reviews"
    }]
      , l = [{
        label: "Discord",
        href: "https://discord.mccapes.net",
        icon: a.FaDiscord
    }, {
        label: "YouTube",
        href: "https://www.youtube.com/@realmccapes",
        icon: a.FaYoutube
    }, {
        label: "Instagram",
        href: "https://www.instagram.com/realmccapes",
        icon: a.FaInstagram
    }, {
        label: "TikTok",
        href: "https://www.tiktok.com/@realmccapes",
        icon: a.FaTiktok
    }];
    e.s(["default", 0, () => (0,
    t.jsx)("footer", {
        className: "relative overflow-hidden border-t-2 border-[var(--color-ink)] bg-[#1d1a16] py-14 text-neutral-200",
        children: (0,
        t.jsxs)("div", {
            className: "container relative z-10 mx-auto px-6",
            children: [(0,
            t.jsxs)("div", {
                className: "grid grid-cols-1 gap-8 md:grid-cols-4",
                children: [(0,
                t.jsxs)("div", {
                    children: [(0,
                    t.jsx)("div", {
                        className: "mb-4",
                        children: (0,
                        t.jsx)(r.default, {
                            src: "/mccapes_text_logo.png",
                            alt: "MC Capes",
                            width: 1581,
                            height: 286,
                            className: "h-8 w-auto"
                        })
                    }), (0,
                    t.jsx)("p", {
                        className: "mb-4 text-neutral-300",
                        children: "The safest way to buy your Minecraft capes."
                    }), (0,
                    t.jsx)("div", {
                        className: "flex items-center gap-4",
                        children: l.map( ({label: e, href: r, icon: a}) => (0,
                        t.jsx)("a", {
                            href: r,
                            target: "_blank",
                            rel: "noopener noreferrer",
                            "aria-label": e,
                            className: "text-neutral-300 transition-colors hover:text-white",
                            children: (0,
                            t.jsx)(a, {
                                className: "h-6 w-6"
                            })
                        }, e))
                    })]
                }), (0,
                t.jsxs)("div", {
                    children: [(0,
                    t.jsx)("h5", {
                        className: "mb-4 text-sm font-semibold uppercase tracking-[0.12em] text-neutral-400",
                        children: "Shop"
                    }), (0,
                    t.jsx)("ul", {
                        className: "space-y-2",
                        children: i.map(e => (0,
                        t.jsx)("li", {
                            children: (0,
                            t.jsxs)("a", {
                                href: e.href,
                                className: "flex items-center text-neutral-300 transition-colors hover:text-white",
                                children: [(0,
                                t.jsx)(a.FaChevronRight, {
                                    className: "mr-2 text-xs"
                                }), e.label]
                            })
                        }, e.label))
                    })]
                }), (0,
                t.jsxs)("div", {
                    children: [(0,
                    t.jsx)("h5", {
                        className: "mb-4 text-sm font-semibold uppercase tracking-[0.12em] text-neutral-400",
                        children: "Company"
                    }), (0,
                    t.jsx)("ul", {
                        className: "space-y-2",
                        children: [{
                            label: "FAQ",
                            href: "/faq"
                        }, {
                            label: "Trust Center",
                            href: "/trust"
                        }, {
                            label: "Privacy Policy",
                            href: "/privacy"
                        }, {
                            label: "Terms of Service",
                            href: "/terms"
                        }, {
                            label: "Delivery & Refund Policy",
                            href: "/refunds"
                        }].map(e => (0,
                        t.jsx)("li", {
                            children: (0,
                            t.jsxs)("a", {
                                href: e.href,
                                className: "flex items-center text-neutral-300 transition-colors hover:text-white",
                                children: [(0,
                                t.jsx)(a.FaChevronRight, {
                                    className: "mr-2 text-xs"
                                }), e.label]
                            })
                        }, e.label))
                    })]
                }), (0,
                t.jsxs)("div", {
                    children: [(0,
                    t.jsx)("h5", {
                        className: "mb-4 text-sm font-semibold uppercase tracking-[0.12em] text-neutral-400",
                        children: "Contact"
                    }), (0,
                    t.jsxs)("address", {
                        className: "not-italic space-y-2",
                        children: [(0,
                        t.jsxs)("a", {
                            href: "/about",
                            className: "flex items-center text-neutral-300 transition-colors hover:text-white",
                            children: [(0,
                            t.jsx)(a.FaChevronRight, {
                                className: "mr-2 text-xs"
                            }), "About Us"]
                        }), (0,
                        t.jsxs)("a", {
                            href: "mailto:support@mccapes.net",
                            className: "flex items-center text-neutral-300 transition-colors hover:text-white",
                            children: [(0,
                            t.jsx)(a.FaChevronRight, {
                                className: "mr-2 text-xs"
                            }), "support@mccapes.net"]
                        })]
                    })]
                })]
            }), (0,
            t.jsxs)("div", {
                className: "mt-10 flex flex-col items-center justify-between gap-4 border-t border-white/15 pt-8 md:flex-row md:gap-0",
                children: [(0,
                t.jsxs)("p", {
                    className: "text-sm text-neutral-300",
                    children: ["© 2026 ", (0,
                    t.jsx)(n.NoTranslate, {
                        children: "MCCAPES LLC"
                    }), ". All rights reserved."]
                }), (0,
                t.jsxs)("div", {
                    className: "flex items-center gap-4",
                    children: [(0,
                    t.jsx)("p", {
                        className: "text-sm text-neutral-300",
                        children: "mccapes.net"
                    }), (0,
                    t.jsx)(s.default, {})]
                })]
            })]
        })
    })])
}
, 790905, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(37428)
      , a = e.i(610936)
      , s = e.i(350053)
      , n = e.i(483246)
      , i = e.i(473321);
    e.s(["FormattedText", 0, function({children: e, names: l=[]}) {
        let o = (0,
        s.useProtectTranslatePhrases)(l)
          , c = (0,
        r.useMemo)( () => (0,
        i.parseDiscordInline)(e ?? ""), [e]);
        return (0,
        t.jsx)(t.Fragment, {
            children: function e(s, i, l) {
                return s.map( (s, o) => {
                    let c = `${l}-${o}`;
                    if ("text" === s.type) {
                        var d;
                        let e;
                        return (0,
                        t.jsx)(r.Fragment, {
                            children: (d = s.value,
                            1 !== (e = (0,
                            n.splitTextByProtectTranslatePhrases)(d, i)).length || e[0]?.protect ? e.map( (e, s) => e.protect ? (0,
                            t.jsx)(a.NoTranslate, {
                                children: e.value
                            }, `${c}-${s}`) : (0,
                            t.jsx)(r.Fragment, {
                                children: e.value
                            }, `${c}-${s}`)) : d)
                        }, c)
                    }
                    if ("code" === s.type) {
                        let e = s.children.map(e => "text" === e.type ? e.value : "").join("");
                        return (0,
                        t.jsx)("code", {
                            className: "rounded bg-[var(--surface-muted)] px-1 py-0.5 font-mono text-[0.9em]",
                            children: e
                        }, c)
                    }
                    let u = e(s.children, i, c);
                    switch (s.type) {
                    case "bold":
                        return (0,
                        t.jsx)("strong", {
                            className: "font-semibold",
                            children: u
                        }, c);
                    case "italic":
                        return (0,
                        t.jsx)("em", {
                            children: u
                        }, c);
                    case "underline":
                        return (0,
                        t.jsx)("u", {
                            children: u
                        }, c);
                    case "strike":
                        return (0,
                        t.jsx)("s", {
                            children: u
                        }, c);
                    default:
                        return (0,
                        t.jsx)(r.Fragment, {
                            children: u
                        }, c)
                    }
                }
                )
            }(c, o, "ft")
        })
    }
    ])
}
, 936976, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(319565)
      , a = e.i(117354)
      , s = e.i(585653)
      , n = e.i(109876);
    e.s(["default", 0, () => {
        let {isDark: e, toggleTheme: i} = (0,
        n.useTheme)();
        return (0,
        t.jsx)(a.motion.button, {
            type: "button",
            whileHover: {
                scale: 1.05
            },
            whileTap: {
                scale: .9,
                rotate: -15
            },
            onClick: i,
            "aria-label": e ? "Switch to light mode" : "Switch to dark mode",
            title: e ? "Switch to light mode" : "Switch to dark mode",
            className: "p-2 rounded-full bg-[var(--surface)] text-[var(--primary)] hover:bg-[var(--primary)] hover:text-white transition-colors relative flex items-center justify-center overflow-hidden",
            children: (0,
            t.jsx)("span", {
                className: "relative flex h-[1.125rem] w-[1.125rem] items-center justify-center",
                children: (0,
                t.jsx)(r.AnimatePresence, {
                    mode: "wait",
                    initial: !1,
                    children: e ? (0,
                    t.jsx)(a.motion.span, {
                        initial: {
                            rotate: -90,
                            scale: .3,
                            opacity: 0
                        },
                        animate: {
                            rotate: 0,
                            scale: 1,
                            opacity: 1
                        },
                        exit: {
                            rotate: 90,
                            scale: .3,
                            opacity: 0
                        },
                        transition: {
                            duration: .28,
                            ease: "easeOut"
                        },
                        className: "absolute flex items-center justify-center",
                        children: (0,
                        t.jsx)(s.FaMoon, {
                            className: "text-base"
                        })
                    }, "moon") : (0,
                    t.jsx)(a.motion.span, {
                        initial: {
                            rotate: 90,
                            scale: .3,
                            opacity: 0
                        },
                        animate: {
                            rotate: 0,
                            scale: 1,
                            opacity: 1
                        },
                        exit: {
                            rotate: -90,
                            scale: .3,
                            opacity: 0
                        },
                        transition: {
                            duration: .28,
                            ease: "easeOut"
                        },
                        className: "absolute flex items-center justify-center",
                        children: (0,
                        t.jsx)(s.FaSun, {
                            className: "text-base"
                        })
                    }, "sun")
                })
            })
        })
    }
    ])
}
, 819272, 712137, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(117354)
      , a = e.i(340675)
      , s = e.i(836878)
      , n = e.i(585653)
      , i = e.i(362972)
      , l = e.i(825194)
      , o = e.i(37428)
      , c = e.i(157361);
    let d = (0,
    o.createContext)(null)
      , u = () => (0,
    o.useContext)(d);
    e.s(["ProductCardGroup", 0, ({children: e}) => {
        let r = (0,
        o.useRef)(new Set)
          , [a,s] = (0,
        o.useState)(!1)
          , n = (0,
        o.useCallback)( (e, t) => {
            let a = r.current;
            t ? a.add(e) : a.delete(e),
            s(a.size > 0)
        }
        , [])
          , i = (0,
        o.useMemo)( () => ({
            anyOverlap: a,
            reportOverlap: n
        }), [a, n]);
        return (0,
        t.jsx)(d.Provider, {
            value: i,
            children: e
        })
    }
    , "useProductCardGroup", 0, u], 712137);
    var m = e.i(257439)
      , h = e.i(412753)
      , x = e.i(610936)
      , p = e.i(790905)
      , f = e.i(409321)
      , v = e.i(680097)
      , g = e.i(671577);
    let b = r.motion.create(s.default)
      , y = ({product: e, compact: r, isHovered: s=!1, isStatic: n=!1}) => {
        let i = (0,
        m.resolveCapeTexturePath)(e)
          , l = (0,
        m.resolveProductBackgroundImage)(e)
          , o = (0,
        m.isExternalHttpUrl)(l);
        return (0,
        t.jsxs)("div", {
            className: "absolute inset-0",
            children: [(0,
            t.jsx)(a.default, {
                src: l,
                alt: "",
                fill: !0,
                priority: !1,
                unoptimized: o,
                className: `object-cover ${(0,
                m.getProductBackgroundBlurClasses)(r ? "compact" : "default")}`
            }), !n && (0,
            t.jsx)("div", {
                className: "absolute inset-0",
                children: (0,
                t.jsx)(c.default, {
                    texturePath: i,
                    productSlug: e.slug,
                    compact: !!r,
                    variant: "shop-card",
                    isHovered: s
                })
            })]
        })
    }
    ;
    e.s(["default", 0, ({product: e, styles: s="normal", staticMedia: c=!1}) => {
        let d = (0,
        i.usePathname)()
          , {addItem: w} = (0,
        l.useCart)()
          , [j,N] = (0,
        o.useState)(!1)
          , C = (0,
        o.useRef)(null)
          , [k,P] = (0,
        o.useState)(!1)
          , E = u()
          , S = e?.preorder === !0
          , _ = null == e ? "none" : 0 === e.stock ? "gray" : e.stock <= 3 ? "red" : e.stock <= 5 ? "yellow" : "green"
          , R = e ? S ? (0,
        f.getPreorderStockCardStatusText)(e.stock) : (0,
        f.getNonPreorderStockStatusText)(e.stock, e.stockUnitLabel) : ""
          , A = S || "none" !== _ && "green" !== _;
        (0,
        o.useLayoutEffect)( () => {
            if (!A || "normal" !== s)
                return;
            let e = C.current;
            if (!e)
                return;
            let t = () => P(e.scrollWidth > e.clientWidth);
            t();
            let r = new ResizeObserver(t);
            return r.observe(e),
            () => r.disconnect()
        }
        , [A, s, e?.name, R]),
        (0,
        o.useEffect)( () => {
            if (!E || !e)
                return;
            let t = e.id
              , r = A && "normal" === s && k;
            return E.reportOverlap(t, r),
            () => E.reportOverlap(t, !1)
        }
        , [E, e?.id, A, s, k]);
        let T = E ? E.anyOverlap : k;
        if (!e)
            return null;
        let M = (0,
        v.parseProductBadge)(e.badge)
          , $ = (0,
        m.isCapeProduct)(e)
          , O = `/shop/${e.slug}${"/" === d ? "?from=home" : ""}`
          , L = t => {
            t.preventDefault(),
            t.stopPropagation(),
            w(e)
        }
          , I = "gray" === _ ? "stock-badge stock-badge--muted" : "yellow" === _ ? "stock-badge stock-badge--warning" : "green" === _ ? "stock-badge stock-badge--success" : "stock-badge stock-badge--danger";
        return "article" === s ? (0,
        t.jsxs)(b, {
            href: O,
            className: "group flex cursor-pointer items-center gap-5 glass-effect rounded-2xl shadow-[var(--shadow-card)] p-4 transition-all duration-200 hover:border-[color-mix(in_srgb,var(--primary),var(--border)_55%)] card-hover",
            whileHover: {
                scale: 1.03
            },
            onMouseEnter: () => N(!0),
            onMouseLeave: () => N(!1),
            style: (0,
            g.getCardColorStyle)(e.cardColor),
            children: [(0,
            t.jsxs)("span", {
                className: "sr-only",
                children: ["View ", (0,
                t.jsx)(x.NoTranslate, {
                    children: e.name
                })]
            }), (0,
            t.jsx)("div", {
                className: "relative h-24 w-1/3 flex-shrink-0 overflow-hidden rounded-xl border border-[var(--border)] bg-[color-mix(in_srgb,var(--surface-muted),var(--background)_35%)]",
                children: $ ? (0,
                t.jsx)(y, {
                    product: e,
                    compact: !0,
                    isHovered: j,
                    isStatic: c
                }) : (0,
                t.jsx)(a.default, {
                    src: e.image,
                    alt: e.name,
                    fill: !0,
                    className: "object-cover"
                })
            }), (0,
            t.jsxs)("div", {
                className: "relative flex h-full flex-1 flex-col justify-between",
                children: [A && (0,
                t.jsx)("div", {
                    className: "absolute right-0 top-0 hidden md:block",
                    children: (0,
                    t.jsx)("span", {
                        className: I,
                        children: R
                    })
                }), (0,
                t.jsx)("div", {
                    children: (0,
                    t.jsx)("h4", {
                        className: "text-lg font-semibold text-[var(--foreground)] group-hover:text-[var(--accent-light)]",
                        children: (0,
                        t.jsx)(x.NoTranslate, {
                            children: e.name
                        })
                    })
                }), (0,
                t.jsxs)("div", {
                    className: "mt-4 flex items-center justify-between",
                    children: [(0,
                    t.jsx)("div", {
                        className: "flex min-w-0 items-center gap-2",
                        children: (0,
                        t.jsxs)("span", {
                            className: "text-xl font-bold text-[var(--foreground)]",
                            children: [(0,
                            t.jsx)(h.DisplayPrice, {
                                usdAmount: e.price
                            }), null != e.slashPrice && e.slashPrice > 0 && (0,
                            t.jsx)("span", {
                                className: "ml-2 text-sm text-[var(--color-text-muted)] line-through",
                                children: (0,
                                t.jsx)(h.DisplayPrice, {
                                    usdAmount: e.slashPrice
                                })
                            })]
                        })
                    }), (0,
                    t.jsx)("button", {
                        onClick: L,
                        onMouseDown: e => e.stopPropagation(),
                        className: "btn-accent-fill rounded-lg p-2 transition",
                        children: (0,
                        t.jsx)(n.FaShoppingCart, {
                            size: 16
                        })
                    })]
                })]
            })]
        }, e.id) : (0,
        t.jsxs)(b, {
            href: O,
            className: "group relative flex h-full cursor-pointer flex-col overflow-hidden rounded-2xl border-[1.5px] border-[var(--color-border-dark)] bg-[var(--surface)] shadow-[var(--shadow-card)] card-hover",
            variants: {
                hidden: {
                    opacity: 0,
                    y: 20
                },
                visible: {
                    opacity: 1,
                    y: 0
                }
            },
            transition: {
                type: "spring",
                stiffness: 260,
                damping: 24
            },
            onMouseEnter: () => N(!0),
            onMouseLeave: () => N(!1),
            style: (0,
            g.getCardColorStyle)(e.cardColor),
            children: [(0,
            t.jsxs)("span", {
                className: "sr-only",
                children: ["View ", (0,
                t.jsx)(x.NoTranslate, {
                    children: e.name
                })]
            }), (0,
            t.jsxs)("div", {
                className: "relative h-60 shrink-0 overflow-hidden border-b border-[var(--border)] bg-[color-mix(in_srgb,var(--surface-muted),var(--background)_35%)]",
                children: [$ ? (0,
                t.jsx)(y, {
                    product: e,
                    isHovered: j
                }) : (0,
                t.jsx)(a.default, {
                    src: e.image,
                    alt: e.name,
                    fill: !0,
                    className: "object-cover"
                }), M && (0,
                t.jsx)("span", {
                    className: "product-badge absolute left-3 top-3 z-10",
                    style: {
                        backgroundColor: M.color,
                        borderColor: M.color
                    },
                    children: M.text
                }), A && T && (0,
                t.jsx)("div", {
                    className: "absolute bottom-3 right-3 z-20 hidden md:block",
                    children: (0,
                    t.jsx)("span", {
                        className: I,
                        children: R
                    })
                })]
            }), (0,
            t.jsxs)("div", {
                className: "relative flex flex-1 flex-col p-5",
                children: [A && (0,
                t.jsxs)("div", {
                    ref: C,
                    "aria-hidden": "true",
                    className: "pointer-events-none invisible absolute inset-x-5 top-5 hidden items-start gap-2 whitespace-nowrap md:flex",
                    children: [(0,
                    t.jsx)("h4", {
                        className: "text-2xl",
                        children: e.name
                    }), (0,
                    t.jsx)("span", {
                        className: `shrink-0 ${I}`,
                        children: R
                    })]
                }), A && !T && (0,
                t.jsx)("div", {
                    className: "absolute right-5 top-5 z-20 hidden md:block",
                    children: (0,
                    t.jsx)("span", {
                        className: I,
                        children: R
                    })
                }), (0,
                t.jsxs)("div", {
                    className: "mb-2 flex flex-col items-start gap-1.5 md:hidden",
                    children: [(0,
                    t.jsx)("span", {
                        className: `shrink-0 ${I}`,
                        children: R
                    }), (0,
                    t.jsx)("h4", {
                        className: "min-w-0 text-2xl text-[var(--foreground)] group-hover:text-[var(--accent-light)]",
                        children: (0,
                        t.jsx)(x.NoTranslate, {
                            children: e.name
                        })
                    })]
                }), (0,
                t.jsx)("h4", {
                    className: "mb-2 hidden text-2xl text-[var(--foreground)] group-hover:text-[var(--accent-light)] md:block",
                    children: (0,
                    t.jsx)(x.NoTranslate, {
                        children: e.name
                    })
                }), (0,
                t.jsx)("p", {
                    className: "mb-5 line-clamp-2 text-sm text-[var(--color-text-secondary)]",
                    children: (0,
                    t.jsx)(p.FormattedText, {
                        children: e.description
                    })
                }), (0,
                t.jsxs)("div", {
                    className: "mt-auto flex items-center justify-between",
                    children: [(0,
                    t.jsx)("div", {
                        className: "flex min-w-0 items-center gap-2",
                        children: (0,
                        t.jsxs)("span", {
                            className: "text-2xl font-bold text-[var(--foreground)]",
                            children: [(0,
                            t.jsx)(h.DisplayPrice, {
                                usdAmount: e.price
                            }), null != e.slashPrice && e.slashPrice > 0 && (0,
                            t.jsx)("span", {
                                className: "ml-2 text-sm line-through text-[var(--color-text-muted)]",
                                children: (0,
                                t.jsx)(h.DisplayPrice, {
                                    usdAmount: e.slashPrice
                                })
                            })]
                        })
                    }), (0,
                    t.jsx)("button", {
                        type: "button",
                        onClick: L,
                        className: "btn-accent-fill flex items-center rounded-xl p-2.5 transition",
                        children: (0,
                        t.jsx)(r.motion.div, {
                            whileHover: {
                                scale: 1.08
                            },
                            whileTap: {
                                scale: .93
                            },
                            children: (0,
                            t.jsx)(n.FaShoppingCart, {
                                size: 16
                            })
                        })
                    })]
                })]
            })]
        }, e.id)
    }
    ], 819272)
}
, 247903, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(37428)
      , a = e.i(726912)
      , s = e.i(905302);
    let n = async () => {
        if (window.skinview3d)
            return window.skinview3d;
        if (await new Promise( (e, t) => {
            let r = document.querySelector('script[data-skinview3d="1"]');
            if (r) {
                window.skinview3d && e(),
                r.addEventListener("load", () => e(), {
                    once: !0
                }),
                r.addEventListener("error", () => t(Error("skinview3d script failed to load")), {
                    once: !0
                });
                return
            }
            let a = document.createElement("script");
            a.src = "https://cdn.jsdelivr.net/npm/skinview3d@3.4.1/bundles/skinview3d.bundle.js",
            a.async = !0,
            a.dataset.skinview3d = "1",
            a.onload = () => e(),
            a.onerror = () => t(Error("Unable to load skinview3d CDN bundle")),
            document.head.appendChild(a)
        }
        ),
        !window.skinview3d)
            throw Error("skinview3d global not found after script load");
        return window.skinview3d
    }
    ;
    e.s(["default", 0, function({texturePath: e, mode: i, skinPath: l="/skin.png", pausedAnimation: o=!1, showPlayer: c=!0, productSlug: d}) {
        let u = (0,
        r.useRef)(null)
          , [m,h] = (0,
        r.useState)(!1)
          , [x,p] = (0,
        r.useState)( () => (0,
        s.canUseHardwareAcceleratedWebGL)())
          , f = () => {
            let e = document.createElement("canvas");
            e.width = 64,
            e.height = 64;
            let t = e.getContext("2d");
            return t && t.clearRect(0, 0, 64, 64),
            e.toDataURL("image/png")
        }
        ;
        return (0,
        r.useEffect)( () => {
            let t = u.current;
            if (h(!1),
            !t || !x)
                return;
            let r = !1
              , a = null
              , s = null
              , d = !1
              , m = 0
              , v = 0
              , g = document.createElement("canvas");
            g.style.width = "100%",
            g.style.height = "100%",
            g.style.display = "block",
            t.appendChild(g),
            (async () => {
                try {
                    let d = await n();
                    if (r)
                        return;
                    let u = t.clientWidth || 900
                      , m = t.clientHeight || 630;
                    (a = new d.SkinViewer({
                        canvas: g,
                        width: u,
                        height: m,
                        skin: "elytra" !== i || c ? l : f()
                    })).fov = "elytra" === i ? 39 : 40,
                    a.zoom = 1,
                    a.autoRotate = !1,
                    a.animation = null;
                    let x = "elytra" !== i || c ? l : f();
                    if (await a.loadSkin(x),
                    await a.loadCape(e, "elytra" === i ? {
                        backEquipment: "elytra"
                    } : void 0),
                    d.createOrbitControls && ((s = d.createOrbitControls(a)).enableRotate = !1,
                    s.enableZoom = !1,
                    s.enablePan = !1),
                    ("player" === i || "elytra" === i) && d.WalkingAnimation) {
                        let e = new d.WalkingAnimation;
                        e.speed = "elytra" === i ? .65 : .7,
                        e.paused = o,
                        a.animation = e
                    }
                    if (a.playerObject) {
                        if ("elytra" === i && !c) {
                            let e = a.playerObject;
                            e.traverse?.(e => {
                                let t = (e.name || "").toLowerCase();
                                t.includes("elytra") || t.includes("cape") || void 0 === e.visible || (e.visible = !1)
                            }
                            )
                        }
                        a.playerObject.rotation.y = Math.PI + .55,
                        a.playerObject.rotation.x = 0,
                        a.playerObject.rotation.z = 0,
                        a.playerObject.position && (a.playerObject.position.y = "elytra" === i ? -.22 : -.28)
                    }
                    a.render(),
                    h(!1)
                } catch (e) {
                    console.error("ProductSkinviewViewer failed to initialize", e),
                    h(!0),
                    p(!1)
                }
            }
            )();
            let b = e => {
                a?.playerObject && (d = !0,
                m = e.clientX,
                v = a.playerObject.rotation.y,
                g.setPointerCapture(e.pointerId),
                g.style.cursor = "grabbing")
            }
              , y = e => {
                if (!d || !a?.playerObject)
                    return;
                let t = e.clientX - m;
                a.playerObject.rotation.y = v + .01 * t,
                a.render()
            }
              , w = e => {
                d && (d = !1,
                g.hasPointerCapture(e.pointerId) && g.releasePointerCapture(e.pointerId),
                g.style.cursor = "grab")
            }
              , j = e => {
                e.stopImmediatePropagation(),
                e.stopPropagation()
            }
            ;
            g.style.cursor = "grab",
            g.addEventListener("pointerdown", b),
            g.addEventListener("pointermove", y),
            g.addEventListener("pointerup", w),
            g.addEventListener("pointercancel", w),
            g.addEventListener("pointerleave", w),
            g.addEventListener("wheel", j, {
                capture: !0
            });
            let N = () => {
                if (!a)
                    return;
                let e = t.clientWidth || 900
                  , r = t.clientHeight || 630;
                a.width = e,
                a.height = r,
                a.render()
            }
              , C = "u" > typeof ResizeObserver ? new ResizeObserver( () => N()) : null;
            return C?.observe(t),
            window.addEventListener("resize", N),
            () => {
                r = !0,
                C?.disconnect(),
                window.removeEventListener("resize", N),
                g.removeEventListener("pointerdown", b),
                g.removeEventListener("pointermove", y),
                g.removeEventListener("pointerup", w),
                g.removeEventListener("pointercancel", w),
                g.removeEventListener("pointerleave", w),
                g.removeEventListener("wheel", j, !0),
                g.style.cursor = "",
                s?.dispose?.(),
                a?.dispose?.();
                try {
                    let e = g.getContext("webgl2") || g.getContext("webgl") || g.getContext("experimental-webgl");
                    e?.getExtension("WEBGL_lose_context")?.loseContext()
                } catch {}
                t.contains(g) && t.removeChild(g)
            }
        }
        , [x, i, o, c, l, e]),
        (0,
        t.jsxs)("div", {
            className: "relative h-full w-full",
            children: [(0,
            t.jsx)("div", {
                ref: u,
                className: "h-full w-full"
            }), (!x || m) && (0,
            t.jsx)("div", {
                className: "pointer-events-none absolute inset-0",
                children: (0,
                t.jsx)(a.default, {
                    texturePath: e,
                    productSlug: d,
                    fallbackVariant: "productPage",
                    alt: "",
                    imageClassName: "drop-shadow-[8px_8px_28px_rgba(255,255,255,0.45)]"
                })
            })]
        })
    }
    ])
}
, 413092, 197705, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(432349);
    let a = "https://www.trustpilot.com/review/mccapes.net";
    e.s(["TRUSTPILOT_URL", 0, a, "toReview", 0, function(e) {
        return {
            id: e.id,
            author: e.author,
            country: e.country,
            rating: e.rating,
            title: e.title,
            message: e.message,
            date: e.date.toISOString().slice(0, 10),
            tpId: e.tpId
        }
    }
    , "trustpilotReviewUrl", 0, e => e.tpId ? `https://www.trustpilot.com/reviews/${e.tpId}` : null], 197705);
    var s = e.i(263047)
      , n = e.i(840885);
    e.s(["default", 0, ({className: e}) => {
        let i = (0,
        s.useTRPC)()
          , {data: l} = (0,
        n.useQuery)(i.settings.getTrustpilotRating.queryOptions())
          , {data: o} = (0,
        n.useQuery)(i.settings.getTrustpilotReviewCount.queryOptions());
        return null == l || null == o ? null : (0,
        t.jsxs)("a", {
            href: a,
            target: "_blank",
            rel: "noopener noreferrer",
            className: `inline-flex flex-wrap items-center justify-center gap-2.5 text-lg hover:opacity-80 transition-opacity ${e ?? ""}`,
            children: [(0,
            t.jsx)("span", {
                className: "font-semibold text-[var(--foreground)]",
                children: l >= 4.5 ? "Excellent" : l >= 4 ? "Great" : l >= 3 ? "Average" : l >= 2 ? "Poor" : "Bad"
            }), (0,
            t.jsx)(r.default, {
                rating: l,
                size: 22
            }), (0,
            t.jsxs)("span", {
                className: "text-[var(--color-text-secondary)]",
                children: [l.toFixed(1), " based on ", o, " reviews on", " ", (0,
                t.jsx)("span", {
                    className: "font-semibold",
                    style: {
                        color: "#00b67a"
                    },
                    children: "Trustpilot"
                })]
            })]
        })
    }
    ], 413092)
}
, 432349, e => {
    "use strict";
    var t = e.i(694957);
    let r = ({fill: e, size: r}) => (0,
    t.jsxs)("span", {
        className: "relative flex shrink-0 items-center justify-center overflow-hidden rounded-[3px]",
        style: {
            height: r,
            width: r,
            backgroundColor: "#dcdce6"
        },
        children: [(0,
        t.jsx)("span", {
            className: "absolute inset-y-0 left-0",
            style: {
                width: `${100 * e}%`,
                backgroundColor: "#00b67a"
            }
        }), (0,
        t.jsx)("svg", {
            viewBox: "0 0 24 24",
            className: "relative h-[60%] w-[60%] fill-white",
            children: (0,
            t.jsx)("path", {
                d: "M12 2l2.9 6.9 7.4.6-5.6 4.9 1.7 7.3L12 17.8l-6.4 3.9 1.7-7.3L1.7 9.5l7.4-.6z"
            })
        })]
    });
    e.s(["default", 0, ({rating: e, size: a=18, className: s}) => (0,
    t.jsx)("div", {
        className: `flex gap-1 ${s ?? ""}`,
        role: "img",
        "aria-label": `${e} out of 5 stars`,
        children: Array.from({
            length: 5
        }, (s, n) => {
            let i;
            return (0,
            t.jsx)(r, {
                fill: (i = e - n) >= 1 ? 1 : i <= 0 ? 0 : i,
                size: a
            }, n)
        }
        )
    })])
}
, 148652, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(340675)
      , a = e.i(143450);
    let s = {
        sm: "h-14 w-14",
        md: "h-16 w-16",
        lg: "h-20 w-20"
    };
    e.s(["default", 0, function({videoUrl: e, title: n, thumbnailUrl: i, isPlaying: l, onPlay: o, className: c="", playButtonSize: d="md", mediaRounding: u="rounded-lg", playIconColorClass: m="border-l-[var(--primary)]"}) {
        let h = (0,
        a.toYoutubeEmbedUrl)(e, {
            autoplay: l
        })
          , x = (0,
        a.getYoutubeThumbnailUrl)(e, i)
          , p = s[d];
        return (0,
        t.jsx)("div", {
            className: `relative aspect-video w-full ${c}`,
            onClick: l ? void 0 : o,
            role: l ? void 0 : "button",
            tabIndex: l ? void 0 : 0,
            onKeyDown: l ? void 0 : e => {
                ("Enter" === e.key || " " === e.key) && (e.preventDefault(),
                o())
            }
            ,
            children: !l && x ? (0,
            t.jsxs)(t.Fragment, {
                children: [(0,
                t.jsx)(r.default, {
                    src: x,
                    alt: n,
                    fill: !0,
                    sizes: "(min-width: 768px) 40vw, 100vw",
                    className: `${u} object-cover`
                }), (0,
                t.jsx)("div", {
                    className: "absolute inset-0 flex items-center justify-center",
                    children: (0,
                    t.jsx)("div", {
                        className: `flex ${p} items-center justify-center rounded-full bg-[var(--surface)] shadow-[var(--shadow-card)] transition-transform hover:scale-[1.03]`,
                        children: (0,
                        t.jsx)("div", {
                            className: `ml-1.5 h-0 w-0 border-y-[10px] border-l-[18px] border-y-transparent ${m}`
                        })
                    })
                })]
            }) : (0,
            t.jsx)("iframe", {
                className: `h-full w-full ${u}`,
                src: h,
                title: n,
                allow: "accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture",
                allowFullScreen: !0
            })
        })
    }
    ])
}
, 296399, e => {
    "use strict";
    let t = Math.tan(46 * Math.PI / 360) / Math.tan(38 * Math.PI / 360)
      , r = 30 * Math.PI / 180;
    e.s(["CAPE_DROP_SHADOW", 0, {
        offsetX: 8,
        offsetY: 8,
        blur: 28,
        color: "rgba(255,255,255,0.45)"
    }, "HERO_CAPE_CAMERA_Z", 0, 3.95, "HERO_CAPE_FOV", 0, 46, "HERO_CAPE_RENDER_HEIGHT", 0, 1024, "HERO_CAPE_RENDER_WIDTH", 0, 640, "HERO_CAPE_ROT_X", 0, -.07, "HERO_CAPE_ROT_Y", 0, -.39, "HERO_CAPE_SCENE_SCALE", 0, t, "PRODUCT_CARD_RENDER_HEIGHT", 0, 700, "PRODUCT_CARD_RENDER_WIDTH", 0, 1e3, "SHOP_CARD_BASE_ROT_Y", 0, r, "SHOP_CARD_CAPE_ROT_X", 0, .01, "getCapeCameraSettings", 0, e => ({
        fov: 50,
        position: {
            x: 0,
            y: "shop-card" === e ? .1 : .15,
            z: "shop-card" === e ? 3.25 : 3.5
        },
        toneMappingExposure: "shop-card" === e ? 1.5 : 1.6
    })])
}
, 863919, e => {
    "use strict";
    let t = "#5c9fd6"
      , r = new Map
      , a = new Map
      , s = async (e, s) => {
        let n = r.get(e);
        if (n)
            return n;
        let i = a.get(e);
        if (i)
            return i;
        let l = new Promise(e => {
            let r = new Image;
            r.decoding = "async",
            r.src = s,
            r.onload = () => {
                try {
                    let a = document.createElement("canvas");
                    a.width = r.naturalWidth || 64,
                    a.height = r.naturalHeight || 32;
                    let s = a.getContext("2d");
                    if (!s)
                        return void e(t);
                    s.drawImage(r, 0, 0);
                    let n = s.getImageData(0, 0, a.width, a.height).data;
                    e((e => {
                        let r = new Map
                          , a = 0
                          , s = 0;
                        for (let t = 0; t < e.length; t += 4) {
                            let n = e[t] / 255
                              , i = e[t + 1] / 255
                              , l = e[t + 2] / 255;
                            if (e[t + 3] / 255 < .35)
                                continue;
                            a++;
                            let o = Math.max(n, i, l)
                              , c = o - Math.min(n, i, l)
                              , d = 0 === o ? 0 : c / o;
                            if (d < .25 && o < .35 && s++,
                            d < .25 || o < .2)
                                continue;
                            let u = 0;
                            c > 0 && (u = o === n ? (i - l) / c % 6 : o === i ? (l - n) / c + 2 : (n - i) / c + 4),
                            u < 0 && (u += 6);
                            let m = Math.round(10 * u)
                              , h = Math.round(6 * d)
                              , x = Math.round(6 * o)
                              , p = `${m}:${h}:${x}`;
                            r.set(p, (r.get(p) ?? 0) + 1)
                        }
                        let n = ""
                          , i = -1;
                        if (r.forEach( (e, t) => {
                            e > i && (i = e,
                            n = t)
                        }
                        ),
                        a > 0 && s / a >= .6)
                            return "#3f82bf";
                        if (!n)
                            return t;
                        let[l,o,c] = n.split(":").map(e => Number(e))
                          , d = Math.min(90, Math.max(55, o / 6 * 100))
                          , u = Math.min(95, Math.max(65, c / 6 * 100));
                        return `hsl(${Math.round(l / 10 * 60)} ${Math.round(d)}% ${Math.round(.55 * u)}%)`
                    }
                    )(n))
                } catch {
                    e(t)
                }
            }
            ,
            r.onerror = () => e(t)
        }
        ).then(t => (r.set(e, t),
        a.delete(e),
        t));
        return a.set(e, l),
        l
    }
    ;
    e.s(["FALLBACK_HERO_CAPE_COLOR", 0, t, "getCachedCapeAccentColor", 0, e => r.get(e), "getCapeAccentColorFromSource", 0, s], 863919)
}
, 671577, e => {
    "use strict";
    e.s(["getCardColorStyle", 0, e => {
        if (!e)
            return;
        let t = {
            backgroundColor: e
        }
          , r = (e => {
            let t, r, a, s = e.trim().replace(/^#/, "");
            if (3 === s.length)
                t = parseInt(s[0] + s[0], 16),
                r = parseInt(s[1] + s[1], 16),
                a = parseInt(s[2] + s[2], 16);
            else {
                if (6 !== s.length)
                    return null;
                t = parseInt(s.slice(0, 2), 16),
                r = parseInt(s.slice(2, 4), 16),
                a = parseInt(s.slice(4, 6), 16)
            }
            return [t, r, a].some(Number.isNaN) ? null : [t, r, a]
        }
        )(e);
        return r && (( (e, t, r) => (299 * e + 587 * t + 114 * r) / 1e3)(...r) >= 128 ? (t["--foreground"] = "#171717",
        t["--color-text-secondary"] = "rgba(0, 0, 0, 0.62)",
        t["--color-text-muted"] = "rgba(0, 0, 0, 0.48)") : (t["--foreground"] = "#ffffff",
        t["--color-text-secondary"] = "rgba(255, 255, 255, 0.72)",
        t["--color-text-muted"] = "rgba(255, 255, 255, 0.55)")),
        t
    }
    ])
}
, 571927, e => {
    "use strict";
    e.s(["countryFlag", 0, function(e) {
        let t = e.trim().toUpperCase();
        return /^[A-Z]{2}$/.test(t) ? t.replace(/./g, e => String.fromCodePoint(127397 + e.charCodeAt(0))) : ""
    }
    ])
}
, 473321, e => {
    "use strict";
    let t = [{
        delim: "**",
        type: "bold"
    }, {
        delim: "__",
        type: "underline"
    }, {
        delim: "~~",
        type: "strike"
    }, {
        delim: "`",
        type: "code",
        raw: !0
    }, {
        delim: "*",
        type: "italic"
    }, {
        delim: "_",
        type: "italic"
    }];
    e.s(["parseDiscordInline", 0, function e(r) {
        let a = []
          , s = r;
        for (; s.length > 0; ) {
            let r = function(e) {
                for (let r = 0; r < e.length; r++)
                    for (let a of t) {
                        if (!e.startsWith(a.delim, r))
                            continue;
                        let t = r + a.delim.length
                          , s = e.indexOf(a.delim, t);
                        if (s > t)
                            return {
                                index: r,
                                rule: a,
                                inner: e.slice(t, s),
                                end: s + a.delim.length
                            }
                    }
                return null
            }(s);
            if (!r) {
                a.push({
                    type: "text",
                    value: s
                });
                break
            }
            r.index > 0 && a.push({
                type: "text",
                value: s.slice(0, r.index)
            });
            let n = "raw" in r.rule && r.rule.raw ? [{
                type: "text",
                value: r.inner
            }] : e(r.inner);
            a.push({
                type: r.rule.type,
                children: n
            }),
            s = s.slice(r.end)
        }
        return a
    }
    ])
}
, 680097, e => {
    "use strict";
    let t = "#4ade80";
    e.s(["DEFAULT_PRODUCT_BADGE_COLOR", 0, t, "parseProductBadge", 0, function(e) {
        if (!e || "object" != typeof e || Array.isArray(e) || "string" != typeof e.text || "" === e.text.trim())
            return null;
        let r = "string" == typeof e.color && "" !== e.color.trim() ? e.color : t;
        return {
            text: e.text,
            color: r
        }
    }
    ])
}
, 409321, e => {
    "use strict";
    e.s(["getNonPreorderStockStatusText", 0, (e, t) => {
        let r = t?.trim() || "in stock";
        return e >= 6 ? "In stock" : e > 0 ? `${e} ${r}` : "Out of stock"
    }
    , "getPreorderStockCardStatusText", 0, e => e > 0 ? `${e} available` : "Unavailable", "getPreorderStockStatusText", 0, e => e > 0 ? `${e} preorder${e > 1 ? "s" : ""} available` : "No preorders available", "getStockStatusTone", 0, e => e >= 6 ? "green" : e >= 4 ? "yellow" : e >= 1 ? "red" : "gray"])
}
, 128318, e => {
    "use strict";
    let t = "mccapes.skinUsername"
      , r = e => e.replace(/[^a-zA-Z0-9_]/g, "").slice(0, 16);
    e.s(["getStoredSkinUsername", 0, () => {
        try {
            let e = window.localStorage.getItem(t) ?? "";
            return r(e)
        } catch {
            return ""
        }
    }
    , "sanitizeMinecraftUsername", 0, r, "setStoredSkinUsername", 0, e => {
        try {
            e ? window.localStorage.setItem(t, e) : window.localStorage.removeItem(t)
        } catch {}
    }
    ])
}
, 77983, e => {
    "use strict";
    e.i(570002);
    var t = e.i(143450);
    let r = "https://www.googleapis.com/youtube/v3"
      , a = "AIzaSyDnpHEsXsrVgM-1GN0SlkWRosZP9gEwS4U"
      , s = e => {
        let t = parseInt(e);
        return t >= 1e6 ? `${(t / 1e6).toFixed(1)}M` : t >= 1e3 ? `${(t / 1e3).toFixed(1)}K` : e
    }
      , n = async e => {
        if (0 === e.length)
            return [];
        if (!a)
            return console.error("YouTube API key is not configured"),
            [];
        let t = Array.from(new Set(e))
          , n = [];
        try {
            for (let e = 0; e < t.length; e += 50) {
                let i = t.slice(e, e + 50)
                  , l = await fetch(`${r}/channels?part=snippet,statistics&id=${i.join(",")}&key=${a}`);
                if (!l.ok)
                    throw Error(`HTTP error! status: ${l.status}`);
                for (let e of (await l.json()).items)
                    n.push({
                        id: e.id,
                        url: `https://www.youtube.com/channel/${e.id}`,
                        name: e.snippet.title,
                        subscribers: s(e.statistics.subscriberCount),
                        subscriberCount: parseInt(e.statistics.subscriberCount, 10) || 0,
                        thumbnailUrl: e.snippet.thumbnails.medium.url
                    })
            }
        } catch (e) {
            console.error("Error fetching YouTube data:", e)
        }
        return n
    }
      , i = async e => {
        let t = function(e) {
            let t = e.trim();
            if (!t)
                return null;
            if (/^UC[\w-]{22}$/.test(t))
                return {
                    id: t
                };
            if (/^@[\w.-]+$/.test(t))
                return {
                    handle: t
                };
            try {
                let e = new URL(t)
                  , r = e.pathname.match(/\/channel\/(UC[\w-]{22})/);
                if (r)
                    return {
                        id: r[1]
                    };
                let a = e.pathname.match(/\/(@[\w.-]+)/);
                if (a)
                    return {
                        handle: a[1]
                    };
                let s = e.pathname.match(/\/user\/([\w-]+)/);
                if (s)
                    return {
                        username: s[1]
                    }
            } catch {}
            return null
        }(e);
        if (!t || !a)
            return null;
        let s = new URLSearchParams({
            part: "snippet,statistics",
            key: a
        });
        t.id ? s.set("id", t.id) : t.handle ? s.set("forHandle", t.handle) : t.username && s.set("forUsername", t.username);
        try {
            let e = await fetch(`${r}/channels?${s.toString()}`);
            if (!e.ok)
                return null;
            let t = await e.json()
              , a = t.items?.[0];
            if (!a)
                return null;
            return {
                id: a.id,
                name: a.snippet.title,
                thumbnailUrl: a.snippet.thumbnails.medium.url,
                subscriberCount: parseInt(a.statistics.subscriberCount, 10) || 0
            }
        } catch (e) {
            return console.error("Error resolving YouTube channel:", e),
            null
        }
    }
      , l = async e => {
        let s = (0,
        t.getYoutubeID)(e);
        if (!s || !a)
            return null;
        try {
            let e = await fetch(`${r}/videos?part=snippet&id=${s}&key=${a}`);
            if (!e.ok)
                return null;
            let t = await e.json()
              , n = t.items?.[0];
            if (!n)
                return null;
            return {
                videoId: s,
                title: n.snippet.title,
                channelTitle: n.snippet.channelTitle,
                thumbnailUrl: n.snippet.thumbnails.maxres?.url ?? n.snippet.thumbnails.high?.url ?? `https://img.youtube.com/vi/${s}/maxresdefault.jpg`
            }
        } catch (e) {
            return console.error("Error resolving YouTube video:", e),
            null
        }
    }
    ;
    e.s(["fetchYouTubeChannels", 0, n, "resolveYoutubeChannel", 0, i, "resolveYoutubeVideo", 0, l])
}
, 143450, e => {
    "use strict";
    let t = e => e.toLowerCase().replace(/[^a-z0-9]/g, "");
    function r(e) {
        let t = e.match(/^.*(?:youtu\.be\/|v\/|u\/\w\/|embed\/|watch\?v=|&v=)([^#&?]*).*/);
        return t && 11 === t[1].length ? t[1] : null
    }
    function a(e) {
        try {
            let t = new URL(e)
              , r = t.searchParams.get("start") ?? t.searchParams.get("t")
              , a = t.hash.startsWith("#t=") ? t.hash.slice(3) : null
              , s = r ?? a;
            if (!s)
                return null;
            if (/^\d+s?$/.test(s))
                return Number(s.replace(/s$/, ""));
            let n = s.match(/^(?:(\d+)h)?(?:(\d+)m)?(?:(\d+)s)?$/);
            if (!n || "" === n[0])
                return null;
            let i = Number(n[1] ?? 0)
              , l = Number(n[2] ?? 0)
              , o = 3600 * i + 60 * l + Number(n[3] ?? 0);
            return o > 0 ? o : null
        } catch {
            return null
        }
    }
    e.s(["getYoutubeID", 0, r, "getYoutubeStartSeconds", 0, a, "getYoutubeThumbnailUrl", 0, function(e, t) {
        if (t)
            return t;
        let a = r(e);
        return a ? `https://img.youtube.com/vi/${a}/maxresdefault.jpg` : ""
    }
    , "sortVideosByCreatorSubscribers", 0, function(e, r, a) {
        let s = new Map(a.map(e => [e.channelId, e.name]))
          , n = new Map;
        for (let e of r) {
            let r = s.get(e.id);
            for (let a of r ? [e.name, r] : [e.name])
                n.set(t(a), e.subscriberCount)
        }
        let i = e => n.get(t(e.description)) ?? 0;
        return [...e].sort( (e, t) => i(t) - i(e))
    }
    , "toYoutubeEmbedUrl", 0, function(e, t) {
        let s = r(e);
        if (!s)
            return e;
        let n = new URLSearchParams
          , i = a(e);
        null != i && n.set("start", String(i)),
        t?.autoplay && n.set("autoplay", "1");
        let l = n.toString();
        return l ? `https://www.youtube.com/embed/${s}?${l}` : `https://www.youtube.com/embed/${s}`
    }
    ])
}
, 1321, 104858, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(117354)
      , a = e.i(319565)
      , s = e.i(37428)
      , n = e.i(836878)
      , i = e.i(362972)
      , l = e.i(819272)
      , o = e.i(148652)
      , c = e.i(610936);
    let d = r.motion.create(n.default)
      , u = () => {}
      , m = {
        hidden: {
            opacity: 0,
            y: 15
        },
        visible: {
            opacity: 1,
            y: 0,
            transition: {
                duration: .5
            }
        }
    }
      , h = ({article: e, products: a, hideProduct: s, fromHome: n, isPlaying: i, onPlay: u, staticMedia: h=!1}) => {
        let x = e.description.split("\n\n")
          , p = x[0]
          , f = "right" === e.alignment ? "md:float-right md:ml-8" : "md:float-left md:mr-8"
          , v = `/articles/${e.link}${n ? "?from=home" : ""}`;
        return (0,
        t.jsxs)(t.Fragment, {
            children: [!s && e.productSlug && (0,
            t.jsx)(r.motion.div, {
                className: "mb-8 md:w-1/3 mx-auto",
                variants: m,
                children: (0,
                t.jsx)(l.default, {
                    product: a.find(t => t.slug === e.productSlug),
                    styles: "article",
                    staticMedia: h
                })
            }), (0,
            t.jsx)(r.motion.div, {
                className: "mb-8 text-center md:text-left md:w-4/5 mx-auto",
                variants: m,
                children: (0,
                t.jsx)(r.motion.h3, {
                    className: "text-3xl font-bold mb-4 text-[var(--foreground)]",
                    variants: m,
                    children: (0,
                    t.jsx)(c.ProtectedText, {
                        children: e.title
                    })
                })
            }), (0,
            t.jsxs)(r.motion.div, {
                className: "md:w-4/5 mx-auto mb-8",
                variants: m,
                children: [(0,
                t.jsx)("div", {
                    className: `relative mb-5 w-full overflow-hidden rounded-lg md:mb-4 md:w-1/2 ${f}`,
                    children: (0,
                    t.jsx)(o.default, {
                        videoUrl: e.videoUrl,
                        title: e.title,
                        thumbnailUrl: e.thumbnailUrl,
                        isPlaying: i,
                        onPlay: u,
                        className: "cursor-pointer bg-black"
                    })
                }), (0,
                t.jsx)(r.motion.p, {
                    className: "text-lg text-[var(--color-text-secondary)] mb-4",
                    variants: m,
                    children: (0,
                    t.jsx)(c.ProtectedText, {
                        children: p
                    })
                }), x.slice(1, 3).map( (e, a) => (0,
                t.jsx)(r.motion.p, {
                    className: "hidden mb-4 text-lg text-[var(--color-text-secondary)] md:block",
                    variants: m,
                    children: (0,
                    t.jsx)(c.ProtectedText, {
                        children: e
                    })
                }, a)), (0,
                t.jsx)("div", {
                    className: "clear-both"
                })]
            }), (0,
            t.jsxs)("div", {
                className: "mt-6 gap-4 flex justify-center",
                children: [(0,
                t.jsx)(d, {
                    href: v,
                    className: "minecraft-btn",
                    whileHover: {
                        scale: 1.02
                    },
                    whileTap: {
                        scale: .98
                    },
                    variants: m,
                    children: "Read More"
                }), (0,
                t.jsx)(d, {
                    href: "/articles",
                    className: "minecraft-btn",
                    whileHover: {
                        scale: 1.02
                    },
                    whileTap: {
                        scale: .98
                    },
                    variants: m,
                    children: "View All Articles"
                })]
            })]
        })
    }
    ;
    e.s(["default", 0, ({articles: e, products: n, hideProduct: l=!1}) => {
        let o = (0,
        i.usePathname)()
          , [c,d] = (0,
        s.useState)(0)
          , [m,x] = (0,
        s.useState)(!1)
          , [p,f] = (0,
        s.useState)(0)
          , v = e[c] ?? e[0];
        if (!v)
            return null;
        let g = "/" === o
          , b = () => {
            d(t => 0 === t ? e.length - 1 : t - 1),
            x(!1)
        }
          , y = () => {
            d(t => t === e.length - 1 ? 0 : t + 1),
            x(!1)
        }
        ;
        if (!e.length)
            return null;
        let w = e.length > 1;
        return (0,
        t.jsx)("section", {
            className: `bg-transparent relative px-4 sm:px-6 lg:px-8 pt-16 ${w ? "pb-12" : "pb-16"}`,
            children: (0,
            t.jsxs)("div", {
                className: "container mx-auto relative",
                children: [w && (0,
                t.jsxs)(t.Fragment, {
                    children: [(0,
                    t.jsx)("div", {
                        className: "hidden md:block absolute left-4 top-1/2 transform -translate-y-1/2 z-20",
                        children: (0,
                        t.jsx)("button", {
                            onClick: b,
                            className: "carousel-nav-btn h-10 w-10",
                            children: (0,
                            t.jsx)("svg", {
                                xmlns: "http://www.w3.org/2000/svg",
                                className: "h-3.5 w-3.5 text-[var(--foreground)]",
                                viewBox: "0 0 20 20",
                                fill: "currentColor",
                                children: (0,
                                t.jsx)("path", {
                                    fillRule: "evenodd",
                                    d: "M12.707 5.293a1 1 0 010 1.414L9.414 10l3.293 3.293a1 1 0 01-1.414 1.414l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 0z",
                                    clipRule: "evenodd"
                                })
                            })
                        })
                    }), (0,
                    t.jsx)("div", {
                        className: "hidden md:block absolute right-4 top-1/2 transform -translate-y-1/2 z-20",
                        children: (0,
                        t.jsx)("button", {
                            onClick: y,
                            className: "carousel-nav-btn h-10 w-10",
                            children: (0,
                            t.jsx)("svg", {
                                xmlns: "http://www.w3.org/2000/svg",
                                className: "h-3.5 w-3.5 text-[var(--foreground)]",
                                viewBox: "0 0 20 20",
                                fill: "currentColor",
                                children: (0,
                                t.jsx)("path", {
                                    fillRule: "evenodd",
                                    d: "M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z",
                                    clipRule: "evenodd"
                                })
                            })
                        })
                    })]
                }), (0,
                t.jsxs)("div", {
                    className: "relative",
                    children: [(0,
                    t.jsx)("div", {
                        "aria-hidden": !0,
                        inert: !0,
                        className: "grid grid-cols-1 invisible pointer-events-none",
                        children: e.map( (e, r) => (0,
                        t.jsx)("div", {
                            className: "col-start-1 row-start-1",
                            children: (0,
                            t.jsx)(h, {
                                article: e,
                                products: n,
                                hideProduct: l,
                                fromHome: g,
                                isPlaying: !1,
                                onPlay: u,
                                staticMedia: !0
                            })
                        }, r))
                    }), (0,
                    t.jsx)("div", {
                        className: "absolute inset-0 flex items-center",
                        children: (0,
                        t.jsx)("div", {
                            className: "w-full",
                            children: (0,
                            t.jsx)(a.AnimatePresence, {
                                mode: "wait",
                                custom: p,
                                children: (0,
                                t.jsx)(r.motion.div, {
                                    custom: p,
                                    variants: {
                                        enter: e => ({
                                            x: e > 0 ? 50 : -50,
                                            opacity: 0
                                        }),
                                        center: {
                                            zIndex: 1,
                                            x: 0,
                                            opacity: 1
                                        },
                                        exit: e => ({
                                            zIndex: 0,
                                            x: e < 0 ? 50 : -50,
                                            opacity: 0
                                        })
                                    },
                                    initial: "enter",
                                    animate: "center",
                                    exit: "exit",
                                    transition: {
                                        x: {
                                            duration: .35,
                                            ease: [.22, .61, .36, 1]
                                        },
                                        opacity: {
                                            duration: .15
                                        }
                                    },
                                    drag: "x",
                                    dragConstraints: {
                                        left: 0,
                                        right: 0
                                    },
                                    dragElastic: .2,
                                    onDragEnd: (e, t) => {
                                        window.innerWidth <= 768 && (t.offset.x > 50 ? (f(-1),
                                        b()) : t.offset.x < -50 && (f(1),
                                        y()))
                                    }
                                    ,
                                    className: "relative md:cursor-default cursor-grab active:cursor-grabbing",
                                    children: (0,
                                    t.jsx)(h, {
                                        article: v,
                                        products: n,
                                        hideProduct: l,
                                        fromHome: g,
                                        isPlaying: m,
                                        onPlay: () => x(!0)
                                    })
                                }, c)
                            })
                        })
                    })]
                }), w && (0,
                t.jsx)("div", {
                    className: "flex justify-center mt-6 gap-2",
                    children: e.map( (e, r) => (0,
                    t.jsx)("button", {
                        onClick: () => {
                            d(r),
                            x(!1)
                        }
                        ,
                        className: `h-3 w-3 rounded-full transition-all duration-200 ${r === c ? "scale-125 bg-[var(--primary)]" : "bg-[var(--color-text-muted)] hover:bg-[var(--foreground)]"}`
                    }, r))
                })]
            })
        })
    }
    ], 1321);
    var x = e.i(590368)
      , p = e.i(77983)
      , f = e.i(340675)
      , v = e.i(263047)
      , g = e.i(840885);
    e.s(["default", 0, () => {
        let e = (0,
        v.useTRPC)()
          , a = (0,
        g.useQuery)(e.partner.getAll.queryOptions())
          , [i,l] = (0,
        s.useState)([])
          , [o,d] = (0,
        s.useState)(!0);
        return ((0,
        s.useEffect)( () => {
            a.data && (async () => {
                l(await (0,
                p.fetchYouTubeChannels)(a.data.map(e => e.channelId))),
                d(!1)
            }
            )()
        }
        , [a.data]),
        o) ? (0,
        t.jsx)("div", {
            className: "flex justify-center items-center min-h-[200px]",
            children: (0,
            t.jsx)("div", {
                className: "loading-spinner",
                "aria-hidden": "true"
            })
        }) : 0 === i.length ? null : (0,
        t.jsxs)(t.Fragment, {
            children: [(0,
            t.jsx)(x.default, {
                gradient: !1,
                speed: 30,
                className: "py-4 overflow-hidden",
                children: i.map(e => (0,
                t.jsxs)("div", {
                    className: "flex flex-col items-center mx-8 cursor-pointer transition-transform duration-200 hover:scale-[1.02] group",
                    onClick: () => window.open(e.url, "_blank"),
                    children: [(0,
                    t.jsx)("div", {
                        className: "w-32 h-32 relative mb-4",
                        children: (0,
                        t.jsx)(r.motion.div, {
                            className: "relative w-full h-full overflow-hidden bg-[var(--surface-muted)] rounded-full border-2 border-[var(--color-ink)] shadow-[3px_3px_0_0_var(--color-ink)] transition-shadow duration-200 group-hover:shadow-[5px_5px_0_0_var(--color-ink)]",
                            transition: {
                                duration: .6
                            },
                            children: (0,
                            t.jsx)(f.default, {
                                src: e.thumbnailUrl,
                                alt: e.name,
                                fill: !0,
                                sizes: "128px",
                                className: "rounded-full",
                                style: {
                                    objectFit: "cover"
                                }
                            })
                        })
                    }), (0,
                    t.jsx)("h4", {
                        className: "text-lg font-semibold text-[var(--foreground)] mb-1 transition-all duration-300 group-hover:font-bold",
                        children: (0,
                        t.jsx)(c.NoTranslate, {
                            children: e.name
                        })
                    }), (0,
                    t.jsxs)("p", {
                        className: "text-[var(--color-text-secondary)] text-sm",
                        children: [(0,
                        t.jsx)("span", {
                            className: "font-bold",
                            children: e.subscribers
                        }), " ", (0,
                        t.jsx)("span", {
                            className: "font-normal",
                            children: "subscribers"
                        })]
                    })]
                }, e.id))
            }), (0,
            t.jsx)("div", {
                className: "flex justify-center mt-8",
                children: (0,
                t.jsx)(n.default, {
                    href: "/partners",
                    className: "minecraft-btn text-sm px-5 py-2",
                    children: "View All"
                })
            })]
        })
    }
    ], 104858)
}
, 549943, e => {
    "use strict";
    var t = e.i(694957)
      , r = e.i(448358)
      , a = e.i(263047)
      , s = e.i(1321)
      , n = e.i(37428)
      , i = e.i(930611)
      , l = e.i(709684)
      , o = e.i(726912)
      , c = e.i(905302)
      , d = e.i(296399);
    let u = ({quality: e="auto", interactive: r=!0, className: a, texturePath: s="/cape-textures/experience-cape.png", productSlug: u, isHovered: m=!1}) => {
        let h = (0,
        n.useRef)(null)
          , x = (0,
        n.useRef)(!1)
          , [p,f] = (0,
        n.useState)(!1)
          , [v,g] = (0,
        n.useState)( () => (0,
        c.canUseHardwareAcceleratedWebGL)())
          , b = (0,
        n.useMemo)( () => window.matchMedia("(prefers-reduced-motion: reduce)").matches, []);
        return (0,
        n.useEffect)( () => {
            x.current = m
        }
        , [m]),
        (0,
        n.useEffect)( () => {
            let t = h.current;
            if (f(!1),
            !t || !v)
                return;
            let a = !0
              , n = null
              , o = null
              , c = null
              , u = null;
            try {
                let m = t.clientWidth || 520
                  , h = t.clientHeight || 520
                  , p = new i.Scene
                  , v = new i.PerspectiveCamera(d.HERO_CAPE_FOV,m / h,.1,100);
                v.position.set(0, 0, d.HERO_CAPE_CAMERA_Z),
                v.lookAt(0, 0, 0),
                (n = new l.WebGLRenderer({
                    antialias: !0,
                    alpha: !0
                })).setSize(m, h);
                let y = window.innerWidth <= 768
                  , w = b || y
                  , j = "high" === e ? 2 : "low" === e || w ? 1 : 1.7;
                n.setPixelRatio(Math.min(window.devicePixelRatio, j)),
                n.setClearColor(0, 0),
                n.domElement.style.filter = "drop-shadow(0 14px 20px rgba(20, 18, 16, 0.33)) drop-shadow(0 2px 10px rgba(38, 35, 32, 0.3))",
                n.toneMapping = i.ACESFilmicToneMapping,
                n.toneMappingExposure = 1.38,
                n.outputColorSpace = i.SRGBColorSpace,
                t.appendChild(n.domElement),
                p.add(new i.AmbientLight(0xffffff,.8));
                let N = new i.HemisphereLight(0xf6fffb,0xd2e6db,.5);
                p.add(N);
                let C = new i.DirectionalLight(0xdafbef,1);
                C.position.set(3.8, 2.5, 2.1),
                p.add(C);
                let k = new i.DirectionalLight(0xe7ffe9,.72);
                k.position.set(-1.8, 1.6, 2.5),
                p.add(k);
                let P = new i.DirectionalLight(0xe7fff5,.45);
                P.position.set(-2, -1.2, -2.8),
                p.add(P);
                let E = new i.DirectionalLight(0xffffff,.4);
                E.position.set(0, .3, 3.2),
                p.add(E);
                let S = (o = new i.BoxGeometry(1.45,2.3,.16)).attributes.uv.array
                  , _ = e => 1 - (e - 1) / 32
                  , R = (e, t, r, a, s) => {
                    let n = (t - 1) / 64
                      , i = (Math.max(t, a) + 1 - 1) / 64
                      , l = _(r)
                      , o = _(Math.max(r, s) + 1);
                    S[e + 0] = n,
                    S[e + 1] = l,
                    S[e + 2] = i,
                    S[e + 3] = l,
                    S[e + 4] = n,
                    S[e + 5] = o,
                    S[e + 6] = i,
                    S[e + 7] = o
                }
                ;
                R(0, 12, 2, 12, 17),
                R(8, 1, 2, 1, 17),
                R(16, 1, 2, 1, 11),
                R(24, 1, 12, 1, 21),
                R(32, 2, 2, 11, 17),
                R(40, 13, 2, 22, 17),
                o.attributes.uv.needsUpdate = !0;
                let A = null;
                new i.TextureLoader().load(s, e => {
                    if (!a)
                        return;
                    e.magFilter = i.NearestFilter,
                    e.minFilter = i.NearestFilter,
                    e.colorSpace = i.SRGBColorSpace;
                    let t = new i.MeshPhysicalMaterial({
                        map: e,
                        roughness: .44,
                        metalness: .02,
                        clearcoat: .5,
                        clearcoatRoughness: .35
                    });
                    c = t,
                    u = e,
                    (A = new i.Mesh(o,t)).rotation.x = -.07,
                    A.rotation.y = -.39,
                    A.position.set(0, 0, 0),
                    p.add(A),
                    f(!0)
                }
                , void 0, () => {
                    a && g(!1)
                }
                );
                let T = r && !w
                  , M = () => {
                    let e = t.clientWidth || 520
                      , r = t.clientHeight || 520;
                    v.aspect = e / r,
                    v.updateProjectionMatrix(),
                    n.setSize(e, r, !1)
                }
                  , $ = "u" > typeof ResizeObserver ? new ResizeObserver( () => M()) : null;
                $?.observe(t),
                window.addEventListener("resize", M);
                let O = 0
                  , L = () => {
                    if (a) {
                        if (O = requestAnimationFrame(L),
                        A) {
                            A.rotation.y += (-.39 - A.rotation.y) * .08,
                            A.rotation.x += (-.07 - A.rotation.x) * .08;
                            let e = T && x.current ? 1.05 : 1
                              , t = A.scale.x + (e - A.scale.x) * .08;
                            A.scale.setScalar(t),
                            A.position.y = 0
                        }
                        n.render(p, v)
                    }
                }
                ;
                return L(),
                () => {
                    a = !1,
                    cancelAnimationFrame(O),
                    $?.disconnect(),
                    window.removeEventListener("resize", M),
                    n && t.contains(n.domElement) && t.removeChild(n.domElement),
                    n?.forceContextLoss(),
                    n?.dispose(),
                    o?.dispose(),
                    c?.dispose(),
                    u?.dispose()
                }
            } catch (e) {
                console.error("HeroCapeViewer failed to initialize", e),
                a = !1,
                n?.forceContextLoss(),
                n?.dispose(),
                o?.dispose(),
                g(!1)
            }
        }
        , [r, e, b, s, v]),
        (0,
        t.jsxs)("div", {
            className: `relative h-full w-full ${a ?? ""}`,
            children: [(0,
            t.jsx)("div", {
                ref: h,
                className: "relative h-full w-full"
            }), (!v || !p) && (0,
            t.jsx)("div", {
                className: "pointer-events-none absolute inset-0",
                children: (0,
                t.jsx)(o.default, {
                    texturePath: s,
                    productSlug: u,
                    alt: "",
                    imageClassName: "drop-shadow-[0_14px_20px_rgba(20,18,16,0.33)]"
                })
            })]
        })
    }
    ;
    var m = e.i(825194)
      , h = e.i(863919)
      , x = e.i(319565)
      , p = e.i(117354)
      , f = e.i(836878)
      , v = e.i(362972)
      , g = e.i(340675)
      , b = e.i(585653)
      , y = e.i(257439)
      , w = e.i(680610)
      , j = e.i(412753)
      , N = e.i(610936)
      , C = e.i(790905);
    let k = {
        id: "hero-fallback",
        slug: "experience",
        name: "Experience Cape Code",
        description: "The Minecraft Experience Cape is a piece of Minecraft History. The Cape is only obtainable via going to an IRL Minecraft Event, the same as how Minecon Capes were obtainable, which are now worth thousands of dollars. Don't miss out, buy now!",
        price: 49.99,
        slashPrice: 84.99,
        image: "/mc_bg.webp"
    }
      , P = ({heroProducts: e}) => {
        let r = (0,
        v.useRouter)()
          , {addItem: a} = (0,
        m.useCart)()
          , [s,i] = (0,
        n.useState)(0)
          , [l,o] = (0,
        n.useState)({})
          , [P,E] = (0,
        n.useState)(!1)
          , [S,_] = (0,
        n.useState)(!1)
          , [R] = (0,
        n.useState)( () => (0,
        c.canUseHardwareAcceleratedWebGL)())
          , A = (0,
        n.useMemo)( () => R ? e : e.filter(e => !(0,
        y.isCapeProduct)(e) || (0,
        w.hasGeneratedCapeFallbackRenderPath)((0,
        y.resolveCapeTexturePath)(e), e.slug)), [R, e])
          , T = A.length > 0
          , M = T ? A : [k]
          , $ = M.length > 0 ? s % M.length : 0
          , O = M[$] ?? M[0]
          , L = (O?.name?.trim() ?? "Cape Code").match(/^(.+)\s+(Cape(?:\s+\S+)?)$/i)
          , I = (L?.[1]?.trim() ?? "") || ""
          , F = L?.[2]?.trim() || "Cape Code"
          , z = O?.slug
          , H = O && T ? (0,
        y.resolveCapeTexturePath)(O) : "/cape-textures/experience-cape.png"
          , U = !O || (0,
        y.isCapeProduct)(O)
          , D = P || S
          , B = z ? l[z] ?? (0,
        h.getCachedCapeAccentColor)(z) ?? h.FALLBACK_HERO_CAPE_COLOR : h.FALLBACK_HERO_CAPE_COLOR;
        (0,
        n.useEffect)( () => {
            if (!z || l[z] || (0,
            h.getCachedCapeAccentColor)(z))
                return;
            let e = !1;
            return (0,
            h.getCapeAccentColorFromSource)(z, H).then(t => {
                e || o(e => e[z] ? e : {
                    ...e,
                    [z]: t
                })
            }
            ),
            () => {
                e = !0
            }
        }
        , [z, H, l]),
        (0,
        n.useEffect)( () => {
            if (A.length <= 1 || D)
                return;
            let e = setInterval( () => {
                i(e => (e + 1) % A.length)
            }
            , 3e3);
            return () => clearInterval(e)
        }
        , [A.length, D]);
        let Y = T && O ? `/shop/${O.slug}` : "/shop/experience-cape";
        return (0,
        t.jsx)("section", {
            className: "relative -mt-3 w-full overflow-visible px-4 pb-8 pt-0 md:-mt-4 md:px-8 md:pb-12 md:pt-0 lg:min-h-[calc(100svh-6rem)]",
            children: (0,
            t.jsx)("div", {
                className: "container mx-auto max-w-[1320px]",
                children: (0,
                t.jsxs)("div", {
                    className: "grid grid-cols-1 items-center gap-6 lg:min-h-[calc(100svh-8rem)] lg:grid-cols-[1fr_1fr] lg:gap-8",
                    children: [(0,
                    t.jsxs)(p.motion.div, {
                        initial: {
                            opacity: 0,
                            y: 18
                        },
                        animate: {
                            opacity: 1,
                            y: 0
                        },
                        transition: {
                            duration: .45
                        },
                        className: "relative z-10 mx-auto w-full max-w-xl order-2 lg:order-1",
                        children: [(0,
                        t.jsx)(x.AnimatePresence, {
                            mode: "wait",
                            children: (0,
                            t.jsxs)(p.motion.div, {
                                initial: {
                                    opacity: 0,
                                    y: 10
                                },
                                animate: {
                                    opacity: 1,
                                    y: 0
                                },
                                exit: {
                                    opacity: 0,
                                    y: -10
                                },
                                transition: {
                                    duration: .32,
                                    ease: "easeInOut"
                                },
                                children: [(0,
                                t.jsx)("h2", {
                                    className: "mb-2 text-4xl text-[var(--foreground)] md:mb-3 md:text-6xl lg:text-7xl",
                                    children: (0,
                                    t.jsxs)(N.NoTranslate, {
                                        children: [(0,
                                        t.jsxs)("span", {
                                            className: "block whitespace-nowrap",
                                            children: ["The", " ", I ? (0,
                                            t.jsx)("span", {
                                                style: {
                                                    color: B
                                                },
                                                children: I
                                            }) : null]
                                        }), (0,
                                        t.jsx)("span", {
                                            className: "block",
                                            children: F
                                        })]
                                    })
                                }), (0,
                                t.jsx)("p", {
                                    className: "max-w-xl h-[6.4em] overflow-hidden text-sm leading-[1.65] text-[var(--color-text-secondary)] md:h-[6.8em] md:text-lg md:leading-[1.7]",
                                    children: O?.description ? (0,
                                    t.jsx)(C.FormattedText, {
                                        children: O.description
                                    }) : "Purchase a redeemable Minecraft cape code at competitive community pricing without risky third-party marketplaces."
                                })]
                            }, O?.id ?? "hero-copy-default")
                        }), (0,
                        t.jsxs)("div", {
                            className: "mt-6 flex flex-col gap-4 border-b border-[var(--border)] pb-5 md:mt-8 md:gap-6 md:pb-6",
                            children: [(0,
                            t.jsx)(x.AnimatePresence, {
                                mode: "wait",
                                children: (0,
                                t.jsx)(p.motion.div, {
                                    initial: {
                                        opacity: 0,
                                        y: 8
                                    },
                                    animate: {
                                        opacity: 1,
                                        y: 0
                                    },
                                    exit: {
                                        opacity: 0,
                                        y: -8
                                    },
                                    transition: {
                                        duration: .28,
                                        ease: "easeInOut"
                                    },
                                    className: "min-w-0",
                                    children: (0,
                                    t.jsxs)("div", {
                                        className: "flex flex-wrap items-end gap-2 md:gap-3",
                                        children: [(0,
                                        t.jsx)("span", {
                                            className: "block text-4xl font-bold leading-none text-[var(--foreground)] md:text-5xl",
                                            children: (0,
                                            t.jsx)(j.DisplayPrice, {
                                                usdAmount: O.price
                                            })
                                        }), O?.slashPrice != null && O.slashPrice > 0 ? (0,
                                        t.jsx)("span", {
                                            className: "pb-1 text-sm font-semibold text-[var(--color-text-muted)] line-through md:pb-2 md:text-lg",
                                            children: (0,
                                            t.jsx)(j.DisplayPrice, {
                                                usdAmount: O.slashPrice
                                            })
                                        }) : null]
                                    })
                                }, O?.id ?? "hero-price-default")
                            }), (0,
                            t.jsxs)("div", {
                                className: "flex w-full items-center gap-2",
                                children: [(0,
                                t.jsx)(p.motion.button, {
                                    className: "minecraft-btn minecraft-btn--accent min-w-[7.5rem] shrink-0 whitespace-nowrap px-4 py-2 text-sm md:px-6 md:py-2.5 md:text-base",
                                    whileHover: {
                                        scale: 1.02
                                    },
                                    whileTap: {
                                        scale: .98
                                    },
                                    onClick: () => {
                                        T && O ? a(A[$], 1, {
                                            onComplete: () => r.push("/cart")
                                        }) : r.push("/shop/experience-cape")
                                    }
                                    ,
                                    onMouseEnter: () => _(!0),
                                    onMouseLeave: () => _(!1),
                                    onFocus: () => _(!0),
                                    onBlur: () => _(!1),
                                    children: "Buy Now"
                                }), (0,
                                t.jsx)(p.motion.button, {
                                    type: "button",
                                    "aria-label": "Add to cart",
                                    className: "flex h-10 w-10 items-center justify-center rounded-xl border border-[var(--border)] bg-[var(--surface)] text-[var(--foreground)] transition-colors hover:bg-[var(--primary)] hover:text-[var(--text-on-primary)] md:h-11 md:w-11",
                                    whileHover: {
                                        scale: 1.03
                                    },
                                    whileTap: {
                                        scale: .96
                                    },
                                    onClick: () => {
                                        T && O ? a(A[$], 1) : r.push("/shop/experience-cape")
                                    }
                                    ,
                                    onMouseEnter: () => _(!0),
                                    onMouseLeave: () => _(!1),
                                    onFocus: () => _(!0),
                                    onBlur: () => _(!1),
                                    children: (0,
                                    t.jsx)(b.FaShoppingCart, {
                                        size: 14
                                    })
                                })]
                            })]
                        }), (0,
                        t.jsxs)("p", {
                            className: "mt-3 max-w-xl text-xs text-[var(--color-text-muted)] md:mt-4",
                            children: [(0,
                            t.jsx)(N.BrandName, {}), " is not affiliated with", " ", (0,
                            t.jsx)(N.NoTranslate, {
                                children: "Mojang"
                            }), ",", " ", (0,
                            t.jsx)(N.NoTranslate, {
                                children: "Minecraft"
                            }), ", or", " ", (0,
                            t.jsx)(N.NoTranslate, {
                                children: "Microsoft"
                            }), "."]
                        })]
                    }), (0,
                    t.jsx)(p.motion.div, {
                        initial: {
                            opacity: 0,
                            scale: .96
                        },
                        animate: {
                            opacity: 1,
                            scale: 1
                        },
                        transition: {
                            delay: .05,
                            duration: .55
                        },
                        className: "relative z-10 flex h-[370px] w-full items-center justify-center order-1 md:h-[620px] lg:order-2 lg:h-[68vh]",
                        children: (0,
                        t.jsx)(f.default, {
                            href: Y,
                            className: "relative block h-full w-[min(74vw,330px)] md:w-[min(56vw,470px)] lg:w-[min(34vw,500px)] aspect-[10/16] cursor-pointer",
                            "aria-label": O ? `View ${O.name} product page` : "View product page",
                            onMouseEnter: () => E(!0),
                            onMouseLeave: () => E(!1),
                            onFocus: () => E(!0),
                            onBlur: () => E(!1),
                            children: (0,
                            t.jsx)(x.AnimatePresence, {
                                mode: "sync",
                                children: (0,
                                t.jsx)(p.motion.div, {
                                    initial: R ? {
                                        opacity: 0,
                                        rotateY: -360,
                                        scale: .985
                                    } : {
                                        opacity: 1,
                                        rotateY: 0,
                                        scale: 1
                                    },
                                    animate: {
                                        opacity: 1,
                                        rotateY: 0,
                                        scale: 1
                                    },
                                    exit: R ? {
                                        opacity: 0,
                                        rotateY: 360,
                                        scale: .985
                                    } : {
                                        opacity: 1,
                                        rotateY: 0,
                                        scale: 1
                                    },
                                    transition: R ? {
                                        rotateY: {
                                            duration: .42,
                                            ease: [.22, .61, .36, 1]
                                        },
                                        scale: {
                                            duration: .42,
                                            ease: [.22, .61, .36, 1]
                                        },
                                        opacity: {
                                            duration: .3,
                                            ease: "easeInOut",
                                            delay: .04
                                        }
                                    } : {
                                        duration: 0
                                    },
                                    className: "absolute inset-0 h-full w-full",
                                    style: {
                                        transformStyle: "preserve-3d",
                                        willChange: "transform, opacity"
                                    },
                                    children: U ? (0,
                                    t.jsx)("div", {
                                        className: "pointer-events-none absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2",
                                        style: {
                                            height: `${100 * d.HERO_CAPE_SCENE_SCALE}%`,
                                            aspectRatio: "10 / 16"
                                        },
                                        children: (0,
                                        t.jsx)(u, {
                                            quality: "auto",
                                            interactive: !0,
                                            isHovered: P,
                                            texturePath: H,
                                            productSlug: O.slug
                                        })
                                    }) : (0,
                                    t.jsx)(g.default, {
                                        src: O.image,
                                        alt: O.name,
                                        fill: !0,
                                        className: "rounded-3xl object-cover"
                                    })
                                }, O?.slug ?? "hero-cape-default")
                            })
                        })
                    })]
                })
            })
        })
    }
    ;
    var E = e.i(104858)
      , S = e.i(590368)
      , _ = e.i(840885)
      , R = e.i(432349)
      , A = e.i(413092)
      , T = e.i(571927)
      , M = e.i(197705);
    let $ = ({review: e}) => {
        let r = (0,
        T.countryFlag)(e.country);
        return (0,
        t.jsxs)(f.default, {
            href: "/reviews",
            "aria-label": "Read all reviews",
            className: "mx-3 my-2 flex w-[300px] shrink-0 cursor-pointer flex-col gap-3 rounded-2xl border-2 border-[var(--color-ink)] bg-[var(--surface)] p-5 shadow-[5px_5px_0_0_var(--color-ink)] transition-transform hover:-translate-y-0.5",
            children: [(0,
            t.jsx)(R.default, {
                rating: e.rating,
                size: 15
            }), (0,
            t.jsx)("p", {
                className: "line-clamp-3 min-h-[5rem] text-sm leading-relaxed text-[var(--color-text-secondary)]",
                children: (0,
                t.jsx)(N.NoTranslate, {
                    children: e.message || e.title
                })
            }), (0,
            t.jsxs)("div", {
                className: "flex items-center gap-2 text-sm font-semibold text-[var(--foreground)]",
                children: [(0,
                t.jsx)("span", {
                    className: "flex h-6 w-6 shrink-0 items-center justify-center rounded-full border-2 border-[var(--color-ink)] bg-[var(--accent)] text-xs text-white",
                    children: e.author.charAt(0).toUpperCase()
                }), (0,
                t.jsx)(N.NoTranslate, {
                    className: "truncate",
                    children: e.author
                }), r && (0,
                t.jsx)("span", {
                    "aria-hidden": "true",
                    children: r
                })]
            })]
        })
    }
      , O = () => {
        let e = (0,
        a.useTRPC)()
          , {data: r} = (0,
        _.useQuery)(e.review.getAll.queryOptions())
          , s = (r ?? []).map(M.toReview).filter(e => (e.message || e.title).trim().length > 0);
        if (0 === s.length)
            return null;
        let n = Math.ceil(s.length / 2)
          , i = s.length > 4 ? s.slice(0, n) : s
          , l = s.length > 4 ? s.slice(n) : s;
        return (0,
        t.jsxs)("section", {
            className: "relative overflow-hidden px-4 pt-8 pb-16 md:px-8",
            children: [(0,
            t.jsx)("div", {
                className: "container relative z-10 mx-auto",
                children: (0,
                t.jsxs)(p.motion.div, {
                    className: "mb-12 text-center",
                    initial: {
                        opacity: 0,
                        y: 20
                    },
                    whileInView: {
                        opacity: 1,
                        y: 0
                    },
                    viewport: {
                        once: !0
                    },
                    transition: {
                        duration: .5
                    },
                    children: [(0,
                    t.jsx)("h3", {
                        className: "text-5xl text-[var(--foreground)] md:text-6xl",
                        children: "What Players Say"
                    }), (0,
                    t.jsx)(A.default, {
                        className: "mt-3"
                    })]
                })
            }), (0,
            t.jsxs)("div", {
                className: "flex flex-col gap-4",
                children: [(0,
                t.jsx)(S.default, {
                    gradient: !1,
                    speed: 25,
                    pauseOnHover: !0,
                    className: "py-2",
                    children: i.map( (e, r) => (0,
                    t.jsx)($, {
                        review: e
                    }, `row1-${r}`))
                }), (0,
                t.jsx)(S.default, {
                    gradient: !1,
                    speed: 25,
                    direction: "right",
                    pauseOnHover: !0,
                    className: "py-2",
                    children: l.map( (e, r) => (0,
                    t.jsx)($, {
                        review: e
                    }, `row2-${r}`))
                })]
            })]
        })
    }
    ;
    var L = e.i(819272)
      , I = e.i(712137);
    let F = ({products: e}) => {
        let r = (0,
        v.useRouter)();
        return (0,
        t.jsx)("section", {
            id: "our-products",
            className: "relative overflow-hidden px-4 py-18 md:px-8 md:py-24",
            children: (0,
            t.jsxs)("div", {
                className: "container relative z-10 mx-auto",
                children: [(0,
                t.jsxs)(p.motion.div, {
                    className: "mb-14 text-center",
                    initial: {
                        opacity: 0,
                        y: 28
                    },
                    whileInView: {
                        opacity: 1,
                        y: 0
                    },
                    viewport: {
                        once: !0
                    },
                    transition: {
                        duration: .55
                    },
                    children: [(0,
                    t.jsx)("h2", {
                        className: "text-5xl text-[var(--foreground)] md:text-6xl lg:text-7xl",
                        children: "Our Products"
                    }), (0,
                    t.jsx)("p", {
                        className: "mx-auto mt-3 max-w-2xl text-base text-[var(--color-text-secondary)] md:text-lg",
                        children: "Redeemable cape codes with instant email delivery from a trusted source."
                    })]
                }), (0,
                t.jsx)(I.ProductCardGroup, {
                    children: (0,
                    t.jsx)("div", {
                        className: "grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-3",
                        children: e.map( (e, r) => (0,
                        t.jsx)(p.motion.div, {
                            className: "h-full",
                            initial: {
                                opacity: 0,
                                y: 20
                            },
                            whileInView: {
                                opacity: 1,
                                y: 0
                            },
                            viewport: {
                                once: !0,
                                margin: "-80px"
                            },
                            transition: {
                                type: "spring",
                                stiffness: 260,
                                damping: 24,
                                delay: Math.min(.08 * r, .48)
                            },
                            children: (0,
                            t.jsx)(L.default, {
                                product: e
                            })
                        }, e.id))
                    })
                }), (0,
                t.jsx)(p.motion.div, {
                    className: "mt-14 text-center",
                    initial: {
                        opacity: 0,
                        y: 20
                    },
                    whileInView: {
                        opacity: 1,
                        y: 0
                    },
                    viewport: {
                        once: !0
                    },
                    transition: {
                        delay: .2
                    },
                    children: (0,
                    t.jsx)(p.motion.button, {
                        whileTap: {
                            scale: .98
                        },
                        onClick: () => r.push("/shop"),
                        className: "minecraft-btn px-8 py-3 text-sm uppercase tracking-[0.08em]",
                        children: (0,
                        t.jsxs)("span", {
                            className: "inline-flex items-center gap-2 whitespace-nowrap",
                            children: ["Explore All Capes", (0,
                            t.jsx)(b.FaChevronRight, {
                                className: "text-xs",
                                "aria-hidden": "true"
                            })]
                        })
                    })
                })]
            })
        })
    }
    ;
    var z = e.i(247903)
      , H = e.i(128318)
      , U = e.i(409321);
    let D = ({texturePath: e, className: r}) => (0,
    t.jsx)("span", {
        "aria-hidden": "true",
        className: `block ${r ?? ""}`,
        style: {
            backgroundImage: `url('${e}')`,
            backgroundRepeat: "no-repeat",
            backgroundSize: "640% 200%",
            backgroundPosition: "1.85% 6.25%",
            imageRendering: "pixelated"
        }
    })
      , B = () => {
        let e = (0,
        v.useRouter)()
          , {addItem: r} = (0,
        m.useCart)()
          , s = (0,
        a.useTRPC)()
          , {data: i} = (0,
        _.useQuery)(s.product.getAll.queryOptions({
            isProductPage: !0
        }))
          , [l] = (0,
        n.useState)( () => (0,
        c.canUseHardwareAcceleratedWebGL)())
          , o = (0,
        n.useMemo)( () => (i ?? []).filter(e => (0,
        y.isCapeProduct)(e)), [i])
          , [d,u] = (0,
        n.useState)(0)
          , [x,g] = (0,
        n.useState)(!1)
          , [w,C] = (0,
        n.useState)("")
          , [k,P] = (0,
        n.useState)("")
          , [E,S] = (0,
        n.useState)("player")
          , [R,A] = (0,
        n.useState)(null);
        if ((0,
        n.useEffect)( () => {
            if (0 === o.length)
                return;
            let e = o[d % o.length]
              , t = e.slug
              , r = (0,
            h.getCachedCapeAccentColor)(t);
            if (r)
                return void A(r);
            A(null);
            let a = !1;
            return (0,
            h.getCapeAccentColorFromSource)(t, (0,
            y.resolveCapeTexturePath)(e)).then(e => {
                a || A(e)
            }
            ),
            () => {
                a = !0
            }
        }
        , [o, d]),
        (0,
        n.useEffect)( () => {
            let e = (0,
            H.getStoredSkinUsername)();
            e && (P(e),
            C(e))
        }
        , []),
        0 === o.length)
            return null;
        let T = d % o.length
          , M = o[T]
          , $ = (0,
        y.resolveCapeTexturePath)(M)
          , O = (0,
        y.resolveProductBackgroundImage)(M)
          , L = k ? `https://mc-heads.net/skin/${encodeURIComponent(k)}` : "/skin.png"
          , I = M.stock ?? 0
          , F = !0 === M.preorder
          , B = 0 === I ? "gray" : I <= 3 ? "red" : I <= 5 ? "yellow" : "green"
          , Y = F ? (0,
        U.getPreorderStockCardStatusText)(I) : (0,
        U.getNonPreorderStockStatusText)(I, M.stockUnitLabel)
          , q = `/shop/${M.slug}?from=home`
          , V = R ?? (0,
        h.getCachedCapeAccentColor)(M.slug) ?? h.FALLBACK_HERO_CAPE_COLOR
          , W = M.name.match(/^(.+)\s+(Cape(?:\s+\S+)?)$/i)
          , G = W?.[1]?.trim() ?? ""
          , Q = W?.[2]?.trim() ?? ""
          , K = !!(G && Q)
          , X = e => u(t => (t + e + o.length) % o.length)
          , Z = () => {
            let e = (0,
            H.sanitizeMinecraftUsername)(w.trim());
            P(e),
            C(e),
            (0,
            H.setStoredSkinUsername)(e),
            g(!1)
        }
        ;
        return (0,
        t.jsx)("section", {
            id: "try-on",
            className: "relative px-4 py-16 md:px-8",
            children: (0,
            t.jsxs)("div", {
                className: "container mx-auto max-w-[1200px]",
                children: [(0,
                t.jsxs)(p.motion.div, {
                    className: "mb-10 text-center",
                    initial: {
                        opacity: 0,
                        y: 20
                    },
                    whileInView: {
                        opacity: 1,
                        y: 0
                    },
                    viewport: {
                        once: !0
                    },
                    transition: {
                        duration: .5
                    },
                    children: [(0,
                    t.jsx)("h3", {
                        className: "text-5xl text-[var(--foreground)] md:text-6xl",
                        children: "Fitting Room"
                    }), (0,
                    t.jsx)("p", {
                        className: "mx-auto mt-3 max-w-2xl text-[var(--color-text-secondary)]",
                        children: "Spin the player around to preview the cape on your skin."
                    })]
                }), (0,
                t.jsxs)("div", {
                    className: "grid grid-cols-1 gap-6 lg:grid-cols-[1.25fr_1fr]",
                    children: [(0,
                    t.jsxs)("div", {
                        className: "relative aspect-[10/9] overflow-hidden rounded-2xl border-2 border-[var(--color-ink)] shadow-[5px_5px_0_0_var(--color-ink)] md:aspect-[10/8]",
                        children: [(0,
                        t.jsx)("div", {
                            className: `pointer-events-none absolute inset-0 bg-cover bg-center ${(0,
                            y.getProductBackgroundBlurClasses)("default")}`,
                            style: {
                                backgroundImage: `url('${O}')`
                            }
                        }), (0,
                        t.jsx)("div", {
                            className: "pointer-events-none absolute inset-0 bg-black/15"
                        }), (0,
                        t.jsx)("div", {
                            className: "absolute inset-0 z-[2]",
                            children: (0,
                            t.jsx)(z.default, {
                                texturePath: $,
                                productSlug: M.slug,
                                mode: E,
                                skinPath: L
                            })
                        }), (0,
                        t.jsxs)("div", {
                            className: "absolute left-3 top-3 z-10 flex flex-wrap items-center gap-2",
                            children: [k ? (0,
                            t.jsx)("button", {
                                type: "button",
                                onClick: () => g(e => !e),
                                "aria-label": "Change skin",
                                className: "inline-flex h-10 w-10 items-center justify-center overflow-hidden rounded-md border-2 border-[var(--color-ink)] bg-[var(--surface)] shadow-[3px_3px_0_0_var(--color-ink)] transition hover:brightness-105",
                                children: (0,
                                t.jsx)("img", {
                                    src: `https://mc-heads.net/avatar/${encodeURIComponent(k)}/40`,
                                    alt: `${k} avatar`,
                                    className: "h-full w-full object-cover",
                                    onError: e => {
                                        let t = e.currentTarget;
                                        t.src.includes("/Steve/") || (t.src = "https://mc-heads.net/avatar/Steve/40")
                                    }
                                })
                            }) : (0,
                            t.jsx)("button", {
                                type: "button",
                                onClick: () => g(e => !e),
                                className: "font-accent inline-flex items-center rounded-md border-2 border-[var(--color-ink)] bg-[var(--accent)] px-3 py-1 text-xs font-bold uppercase tracking-[0.1em] text-[var(--color-accent-border)] shadow-[3px_3px_0_0_var(--color-ink)] transition hover:brightness-105",
                                children: "See it on your skin"
                            }), x && (0,
                            t.jsxs)("div", {
                                className: "flex items-center gap-1",
                                children: [(0,
                                t.jsx)("input", {
                                    type: "text",
                                    value: w,
                                    onChange: e => C(e.target.value),
                                    onKeyDown: e => {
                                        "Enter" === e.key && Z()
                                    }
                                    ,
                                    maxLength: 16,
                                    placeholder: "Username",
                                    className: "h-8 w-28 rounded-lg border-2 border-[var(--color-ink)] bg-[var(--surface)] px-2 text-xs text-[var(--foreground)] outline-none placeholder:text-[var(--color-text-muted)]"
                                }), (0,
                                t.jsx)("button", {
                                    type: "button",
                                    onClick: Z,
                                    className: "h-8 rounded-lg border-2 border-[var(--color-ink)] bg-[var(--primary)] px-2 text-xs font-semibold text-[var(--text-on-primary)]",
                                    children: "Go"
                                })]
                            })]
                        }), (0,
                        t.jsx)("button", {
                            type: "button",
                            "aria-label": "Previous cape",
                            onClick: () => X(-1),
                            className: "absolute left-3 top-1/2 z-10 flex h-10 w-10 -translate-y-1/2 items-center justify-center rounded-full border-2 border-[var(--color-ink)] bg-[var(--surface)] text-[var(--foreground)] shadow-[var(--shadow-card)] transition hover:bg-[var(--surface-elevated)]",
                            children: (0,
                            t.jsx)(b.FaChevronLeft, {
                                size: 14
                            })
                        }), (0,
                        t.jsx)("button", {
                            type: "button",
                            "aria-label": "Next cape",
                            onClick: () => X(1),
                            className: "absolute right-3 top-1/2 z-10 flex h-10 w-10 -translate-y-1/2 items-center justify-center rounded-full border-2 border-[var(--color-ink)] bg-[var(--surface)] text-[var(--foreground)] shadow-[var(--shadow-card)] transition hover:bg-[var(--surface-elevated)]",
                            children: (0,
                            t.jsx)(b.FaChevronRight, {
                                size: 14
                            })
                        }), l && (0,
                        t.jsx)("div", {
                            className: "absolute bottom-3 left-1/2 z-10 -translate-x-1/2",
                            children: (0,
                            t.jsx)("div", {
                                className: "inline-flex rounded-full border-2 border-[var(--color-ink)] bg-[var(--surface)] p-1 shadow-[3px_3px_0_0_var(--color-ink)]",
                                children: [{
                                    id: "player",
                                    label: "Player"
                                }, {
                                    id: "elytra",
                                    label: "Elytra"
                                }].map( ({id: e, label: r}) => (0,
                                t.jsx)("button", {
                                    type: "button",
                                    onClick: () => S(e),
                                    className: `rounded-full px-4 py-1 text-xs font-bold uppercase tracking-[0.08em] transition ${E === e ? "bg-[var(--accent)] text-[var(--color-accent-border)]" : "text-[var(--color-text-secondary)] hover:text-[var(--foreground)]"}`,
                                    children: r
                                }, e))
                            })
                        })]
                    }), (0,
                    t.jsxs)("div", {
                        className: "flex h-full flex-col justify-center gap-6",
                        children: [(0,
                        t.jsxs)("div", {
                            className: "flex flex-col rounded-2xl border-2 border-[var(--color-ink)] bg-[var(--surface)] p-6 shadow-[5px_5px_0_0_var(--color-ink)]",
                            children: [(0,
                            t.jsx)("span", {
                                className: "font-accent w-fit self-start text-xs font-bold uppercase tracking-[0.1em] text-[var(--color-text-secondary)]",
                                children: "Equip a cape"
                            }), (0,
                            t.jsx)("div", {
                                className: "mt-3 grid gap-1.5",
                                style: {
                                    gridTemplateColumns: `repeat(${o.length}, minmax(0, 1fr))`
                                },
                                children: o.map( (e, r) => (0,
                                t.jsx)("button", {
                                    type: "button",
                                    onClick: () => u(r),
                                    "aria-label": e.name,
                                    title: e.name,
                                    className: `relative aspect-[10/16] overflow-hidden rounded-md border-2 bg-[var(--surface-muted)] transition ${r === T ? "border-[var(--color-accent-border)] ring-2 ring-[var(--accent)]" : "border-[var(--color-ink)] hover:brightness-105"}`,
                                    children: (0,
                                    t.jsx)(D, {
                                        texturePath: (0,
                                        y.resolveCapeTexturePath)(e),
                                        className: "h-full w-full"
                                    })
                                }, e.id))
                            })]
                        }), (0,
                        t.jsxs)(f.default, {
                            href: q,
                            className: "card-hover flex cursor-pointer flex-col rounded-2xl border-2 border-[var(--color-ink)] bg-[var(--surface)] p-6 shadow-[5px_5px_0_0_var(--color-ink)]",
                            children: [(0,
                            t.jsxs)("div", {
                                children: [(0,
                                t.jsx)("h4", {
                                    className: "text-3xl text-[var(--foreground)] md:text-4xl",
                                    children: (0,
                                    t.jsx)(N.NoTranslate, {
                                        children: K ? (0,
                                        t.jsxs)(t.Fragment, {
                                            children: [(0,
                                            t.jsx)("span", {
                                                style: {
                                                    color: V
                                                },
                                                children: G
                                            }), " ", Q]
                                        }) : M.name
                                    })
                                }), (0,
                                t.jsxs)("div", {
                                    className: "mt-2 flex flex-wrap items-center gap-x-3 gap-y-2",
                                    children: [(0,
                                    t.jsxs)("span", {
                                        className: "text-2xl font-bold text-[var(--foreground)]",
                                        children: [(0,
                                        t.jsx)(j.DisplayPrice, {
                                            usdAmount: M.price
                                        }), null != M.slashPrice && M.slashPrice > 0 && (0,
                                        t.jsx)("span", {
                                            className: "ml-2 text-sm text-[var(--color-text-muted)] line-through",
                                            children: (0,
                                            t.jsx)(j.DisplayPrice, {
                                                usdAmount: M.slashPrice
                                            })
                                        })]
                                    }), (F || "green" !== B) && (0,
                                    t.jsx)("span", {
                                        className: "gray" === B ? "stock-badge stock-badge--muted" : "yellow" === B ? "stock-badge stock-badge--warning" : "green" === B ? "stock-badge stock-badge--success" : "stock-badge stock-badge--danger",
                                        children: Y
                                    })]
                                })]
                            }), (0,
                            t.jsxs)("div", {
                                className: "mt-auto flex gap-3 pt-6",
                                children: [(0,
                                t.jsxs)("button", {
                                    type: "button",
                                    onClick: e => {
                                        e.preventDefault(),
                                        e.stopPropagation(),
                                        r(M)
                                    }
                                    ,
                                    className: "flex flex-1 items-center justify-center gap-2 rounded-xl border-2 border-[var(--color-ink)] bg-[var(--surface)] px-4 py-3 font-semibold text-[var(--foreground)] transition hover:bg-[var(--surface-muted)]",
                                    children: [(0,
                                    t.jsx)(b.FaShoppingCart, {
                                        size: 15
                                    }), "Add to cart"]
                                }), (0,
                                t.jsx)("button", {
                                    type: "button",
                                    onClick: t => {
                                        t.preventDefault(),
                                        t.stopPropagation(),
                                        r(M, 1, {
                                            onComplete: () => e.push("/cart")
                                        })
                                    }
                                    ,
                                    className: "minecraft-btn minecraft-btn--accent flex-1 px-4 py-3",
                                    children: "Buy now"
                                })]
                            }), (0,
                            t.jsx)("span", {
                                className: "mt-3 block text-center text-sm font-medium text-[var(--color-text-secondary)] transition-colors hover:text-[var(--accent-light)]",
                                children: "View details"
                            })]
                        })]
                    })]
                })]
            })
        })
    }
      , Y = ({message: e}) => (0,
    t.jsx)("main", {
        className: "flex min-h-screen items-center justify-center bg-[var(--background)]",
        "aria-label": e ?? "Loading",
        children: (0,
        t.jsx)("div", {
            className: "loading-spinner",
            "aria-hidden": "true"
        })
    });
    e.s(["default", 0, () => {
        let e = (0,
        a.useTRPC)()
          , {data: n} = (0,
        _.useQuery)(e.product.getAll.queryOptions({
            isHomePage: !0
        }))
          , {data: i, isLoading: l, isError: o} = (0,
        _.useQuery)(e.product.getAll.queryOptions({
            isProductPage: !0
        }))
          , {data: c} = (0,
        _.useQuery)(e.article.getAll.queryOptions({
            includeInactive: !1
        }));
        return o ? (0,
        t.jsx)(Y, {
            message: "Unable to load the cape catalog. Refresh to try again."
        }) : l || !i ? (0,
        t.jsx)(Y, {}) : (0,
        t.jsxs)("div", {
            className: "relative min-h-screen bg-[var(--background)] text-[var(--foreground)]",
            children: [(0,
            t.jsxs)("section", {
                className: "relative overflow-visible",
                children: [(0,
                t.jsx)("div", {
                    className: "relative z-10",
                    children: (0,
                    t.jsx)(P, {
                        heroProducts: i
                    })
                }), (0,
                t.jsx)(p.motion.button, {
                    type: "button",
                    onClick: () => {
                        let e = document.getElementById("our-products");
                        e && e.scrollIntoView({
                            behavior: "smooth",
                            block: "start"
                        })
                    }
                    ,
                    whileHover: {
                        y: -2
                    },
                    whileTap: {
                        scale: .98
                    },
                    className: "absolute bottom-12 left-1/2 z-30 hidden -translate-x-1/2 rounded-full border border-[var(--border)] bg-[var(--surface)] px-4 py-2 text-xs font-semibold uppercase tracking-[0.1em] text-[var(--color-text-secondary)] transition-colors hover:text-[var(--foreground)] md:bottom-16 md:inline-flex",
                    children: (0,
                    t.jsxs)("span", {
                        className: "inline-flex items-center gap-2",
                        children: ["View all", (0,
                        t.jsx)(b.FaChevronDown, {
                            className: "text-xs opacity-70"
                        })]
                    })
                })]
            }), (0,
            t.jsx)(F, {
                products: n || []
            }), (0,
            t.jsx)(B, {}), (0,
            t.jsx)(O, {}), c && c.length > 0 && (0,
            t.jsx)("section", {
                id: "articles",
                className: "w-full border-y border-[var(--border)] bg-[color-mix(in_srgb,var(--surface),#000_12%)]",
                children: (0,
                t.jsx)("div", {
                    className: "px-2 md:px-6",
                    children: (0,
                    t.jsx)(s.default, {
                        articles: c,
                        products: i
                    })
                })
            }), (0,
            t.jsx)("section", {
                className: "relative overflow-hidden px-4 pt-18 pb-8 md:px-8",
                children: (0,
                t.jsxs)("div", {
                    className: "container relative z-10 mx-auto",
                    children: [(0,
                    t.jsxs)(p.motion.div, {
                        className: "mb-12 text-center",
                        initial: {
                            opacity: 0,
                            y: 20
                        },
                        whileInView: {
                            opacity: 1,
                            y: 0
                        },
                        viewport: {
                            once: !0
                        },
                        transition: {
                            duration: .5
                        },
                        children: [(0,
                        t.jsx)("h3", {
                            className: "text-5xl text-[var(--foreground)] md:text-6xl",
                            children: "Trusted Partners"
                        }), (0,
                        t.jsxs)("p", {
                            className: "mx-auto mt-3 max-w-2xl text-[var(--color-text-secondary)]",
                            children: ["Featured ", (0,
                            t.jsx)(N.NoTranslate, {
                                children: "Minecraft"
                            }), " creators wearing and recommending our capes."]
                        })]
                    }), (0,
                    t.jsx)("div", {
                        className: "px-2 pt-5 md:px-3",
                        children: (0,
                        t.jsx)(E.default, {})
                    })]
                })
            }), (0,
            t.jsx)(r.default, {})]
        })
    }
    ], 549943)
}
]);
