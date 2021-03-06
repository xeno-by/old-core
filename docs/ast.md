We use macro annotations to generate swaths of boilerplate that are required for our abstract syntax trees
to be efficient and convenient. Here's the code that we write in [Trees.scala](/reflection/Trees.scala):

```
@ast class If(cond: Term, thenp: Term, elsep: Term = Lit.Unit()) extends Term
```

Here's the code generated by the `@ast` macro annotation:

```
@_root_.org.scalareflect.ast.internal.astClass @_root_.org.scalareflect.adt.Internal.leafClass final class If private (
  // part 1: several bookkeeping fields
  protected val internalPrototype: If,
  protected val internalParent: _root_.scala.reflect.core.Tree,
  protected val internalScratchpads: _root_.scala.collection.immutable.Map[_root_.scala.reflect.semantic.Host, _root_.scala.collection.immutable.Seq[Any]],
  val origin: _root_.scala.reflect.core.Origin
)(
  // part 2: payload that also includes synthetic companion parameters for defaults
  private var _cond: Term,
  private var _thenp: Term,
  private var _elsep: Term,
  @_root_.org.scalareflect.ast.trivia  @_root_.org.scalareflect.ast.auto private var _hasElsep: _root_.scala.Boolean
) extends Term with _root_.scala.Product {
  // part 3: accessors for bookkeeping fields
  private[core] def internalCopy(prototype: Tree = internalPrototype, parent: Tree = internalParent, scratchpads: _root_.scala.collection.immutable.Map[_root_.scala.reflect.semantic.Host, _root_.scala.collection.immutable.Seq[Any]] = internalScratchpads, origin: _root_.scala.reflect.core.Origin = origin): ThisType = new ThisType(prototype.asInstanceOf[ThisType], parent, internalScratchpads, origin)(_root_.org.scalareflect.ast.internal.initField(this._cond), _root_.org.scalareflect.ast.internal.initField(this._thenp), _root_.org.scalareflect.ast.internal.initField(this._elsep), _root_.org.scalareflect.ast.internal.initField(this._hasElsep));

  // part 4: accessors for the payload
  def cond: Term = {
    _root_.org.scalareflect.ast.internal.loadField(this._cond);
    this._cond
  };
  def thenp: Term = {
    _root_.org.scalareflect.ast.internal.loadField(this._thenp);
    this._thenp
  };
  def elsep: Term = {
    _root_.org.scalareflect.ast.internal.loadField(this._elsep);
    this._elsep
  };
  def hasElsep: _root_.scala.Boolean = {
    _root_.org.scalareflect.ast.internal.loadField(this._hasElsep);
    this._hasElsep
  };
  def copy(cond: Term = this.cond, thenp: Term = this.thenp, elsep: Term = this.elsep)(implicit origin: _root_.scala.reflect.core.Origin): ThisType = If.apply(cond, thenp, elsep)(_root_.scala.reflect.core.Origin.Transform(this, this.origin));

  // part 5: advanced caseclass-like functionality
  override type ThisType = If;

  // part 6: standard caseclass-like functionality
  override def productPrefix: _root_.scala.Predef.String = _root_.org.scalareflect.ast.internal.productPrefix[ThisType];
  override def productArity: _root_.scala.Int = 3;
  override def productElement(n: _root_.scala.Int): Any = n match {
    case 0 => this.cond
    case 1 => this.thenp
    case 2 => this.elsep
    case _ => throw new _root_.scala.IndexOutOfBoundsException(n.toString)
  };
  override def productIterator: _root_.scala.Iterator[_root_.scala.Any] = _root_.scala.runtime.ScalaRunTime.typedProductIterator(this);
  override def canEqual(that: _root_.scala.Any): _root_.scala.Boolean = that.isInstanceOf[ThisType];
  override def equals(that: _root_.scala.Any): _root_.scala.Boolean = this.eq(that.asInstanceOf[AnyRef]);
  override def hashCode: _root_.scala.Int = _root_.java.lang.System.identityHashCode(this)
}
@_root_.org.scalareflect.ast.internal.astCompanion @_root_.org.scalareflect.adt.Internal.leafCompanion object If {
  def apply(cond: Term, thenp: Term, elsep: Term = null)(implicit origin: _root_.scala.reflect.core.Origin): If = {
    def internal(cond: Term, thenp: Term, elsep: Term, @_root_.org.scalareflect.ast.trivia @_root_.org.scalareflect.ast.auto hasElsep: _root_.scala.Boolean): If = {
      _root_.org.scalareflect.adt.Internal.hierarchyCheck[If];
      _root_.org.scalareflect.adt.Internal.nullCheck(cond);
      _root_.org.scalareflect.adt.Internal.nullCheck(thenp);
      _root_.org.scalareflect.adt.Internal.nullCheck(elsep);
      _root_.org.scalareflect.adt.Internal.nullCheck(hasElsep);
      _root_.org.scalareflect.adt.Internal.emptyCheck(cond);
      _root_.org.scalareflect.adt.Internal.emptyCheck(thenp);
      _root_.org.scalareflect.adt.Internal.emptyCheck(elsep);
      _root_.org.scalareflect.adt.Internal.emptyCheck(hasElsep);
      val node = new If(null, null, _root_.scala.collection.immutable.Map(), origin)(_root_.org.scalareflect.ast.internal.initParam(cond), _root_.org.scalareflect.ast.internal.initParam(thenp), _root_.org.scalareflect.ast.internal.initParam(elsep), _root_.org.scalareflect.ast.internal.initParam(hasElsep));
      _root_.org.scalareflect.ast.internal.storeField(node._cond, cond);
      _root_.org.scalareflect.ast.internal.storeField(node._thenp, thenp);
      _root_.org.scalareflect.ast.internal.storeField(node._elsep, elsep);
      _root_.org.scalareflect.ast.internal.storeField(node._hasElsep, hasElsep);
      node
    };
    internal(cond, thenp, if (elsep.!=(null))
      elsep
    else
      Lit.Unit(), elsep.!=(null))
  };
  def unapply(x: If): Option[scala.Tuple3[Term, Term, Term]] = if (x.==(null))
    _root_.scala.None
  else
    _root_.scala.Some(scala.Tuple3(x.cond, x.thenp, x.elsep))
}
```

Here's the same code after typechecking with helper def macros expanded:

П```
@org.scalareflect.ast.internal.astClass @org.scalareflect.adt.Internal.leafClass final class If extends AnyRef with scala.reflect.core.Term with Product {
  <paramaccessor> private[this] val internalPrototype: scala.reflect.core.Term.If = _;
  <stable> <accessor> <paramaccessor> protected def internalPrototype: scala.reflect.core.Term.If = If.this.internalPrototype;
  <paramaccessor> private[this] val internalParent: scala.reflect.core.Tree = _;
  <stable> <accessor> <paramaccessor> protected def internalParent: scala.reflect.core.Tree = If.this.internalParent;
  <paramaccessor> private[this] val internalScratchpads: scala.collection.immutable.Map[scala.reflect.semantic.Host,scala.collection.immutable.Seq[Any]] = _;
  <stable> <accessor> <paramaccessor> protected def internalScratchpads: scala.collection.immutable.Map[scala.reflect.semantic.Host,scala.collection.immutable.Seq[Any]] = If.this.internalScratchpads;
  <paramaccessor> private[this] val origin: reflect.core.Origin = _;
  <stable> <accessor> <paramaccessor> def origin: reflect.core.Origin = If.this.origin;
  <paramaccessor> private[this] var _cond: scala.reflect.core.Term = _;
  <accessor> <paramaccessor> private def _cond: scala.reflect.core.Term = If.this._cond;
  <accessor> <paramaccessor> private def _cond_=(x$1: scala.reflect.core.Term): Unit = If.this._cond = x$1;
  <paramaccessor> private[this] var _thenp: scala.reflect.core.Term = _;
  <accessor> <paramaccessor> private def _thenp: scala.reflect.core.Term = If.this._thenp;
  <accessor> <paramaccessor> private def _thenp_=(x$1: scala.reflect.core.Term): Unit = If.this._thenp = x$1;
  <paramaccessor> private[this] var _elsep: scala.reflect.core.Term = _;
  <accessor> <paramaccessor> private def _elsep: scala.reflect.core.Term = If.this._elsep;
  <accessor> <paramaccessor> private def _elsep_=(x$1: scala.reflect.core.Term): Unit = If.this._elsep = x$1;
  <paramaccessor> private[this] var _hasElsep: Boolean = _;
  <accessor> <paramaccessor> private def _hasElsep: Boolean = If.this._hasElsep;
  <accessor> <paramaccessor> private def _hasElsep_=(x$1: Boolean): Unit = If.this._hasElsep = x$1;
  private def <init>(internalPrototype: scala.reflect.core.Term.If, internalParent: scala.reflect.core.Tree, internalScratchpads: scala.collection.immutable.Map[scala.reflect.semantic.Host,scala.collection.immutable.Seq[Any]], origin: reflect.core.Origin)(_cond: scala.reflect.core.Term, _thenp: scala.reflect.core.Term, _elsep: scala.reflect.core.Term, @org.scalareflect.ast.trivia @org.scalareflect.ast.auto _hasElsep: Boolean): scala.reflect.core.Term.If = {
    If.super.<init>();
    ()
  };
  private[core] def internalCopy(prototype: scala.reflect.core.Tree = If.this.internalPrototype, parent: scala.reflect.core.Tree = If.this.internalParent, scratchpads: scala.collection.immutable.Map[scala.reflect.semantic.Host,scala.collection.immutable.Seq[Any]] = If.this.internalScratchpads, origin: reflect.core.Origin = origin): If.this.ThisType = new If.this.ThisType(prototype.asInstanceOf[If.this.ThisType], parent, If.this.internalScratchpads, origin)((null: scala.reflect.core.Term), (null: scala.reflect.core.Term), (null: scala.reflect.core.Term), (this._hasElsep: Boolean));
  override <synthetic> def internalCopy$default$1: scala.reflect.core.Tree = If.this.internalPrototype;
  override <synthetic> def internalCopy$default$2: scala.reflect.core.Tree = If.this.internalParent;
  override <synthetic> def internalCopy$default$3: scala.collection.immutable.Map[scala.reflect.semantic.Host,scala.collection.immutable.Seq[Any]] = If.this.internalScratchpads;
  override <synthetic> def internalCopy$default$4: reflect.core.Origin = If.this.origin;
  def parent: Option[scala.reflect.core.Tree] = if (If.this.internalParent.!=(null))
    scala.Some.apply[scala.reflect.core.Tree](If.this.internalParent)
  else
    scala.None;
  def cond: scala.reflect.core.Term = {
    (if (this._cond.==(null))
      {
        scala.Predef.require(this.internalPrototype.!=(null));
        this._cond_=({
          <artifact> val qual$19: scala.reflect.core.Term = this.internalPrototype.cond;
          <artifact> val x$99: scala.reflect.core.Term = this.internalPrototype.cond;
          <artifact> val x$100: scala.reflect.core.Term.If = this;
          <artifact> val x$101: Map[scala.reflect.semantic.Host,scala.collection.immutable.Seq[Any]] = qual$19.internalCopy$default$3;
          <artifact> val x$102: reflect.core.Origin = qual$19.internalCopy$default$4;
          qual$19.internalCopy(x$99, x$100, x$101, x$102)
        })
      }
    else
      (): Unit);
    this._cond
  };
  def thenp: scala.reflect.core.Term = {
    (if (this._thenp.==(null))
      {
        scala.Predef.require(this.internalPrototype.!=(null));
        this._thenp_=({
          <artifact> val qual$20: scala.reflect.core.Term = this.internalPrototype.thenp;
          <artifact> val x$103: scala.reflect.core.Term = this.internalPrototype.thenp;
          <artifact> val x$104: scala.reflect.core.Term.If = this;
          <artifact> val x$105: Map[scala.reflect.semantic.Host,scala.collection.immutable.Seq[Any]] = qual$20.internalCopy$default$3;
          <artifact> val x$106: reflect.core.Origin = qual$20.internalCopy$default$4;
          qual$20.internalCopy(x$103, x$104, x$105, x$106)
        })
      }
    else
      (): Unit);
    this._thenp
  };
  def elsep: scala.reflect.core.Term = {
    (if (this._elsep.==(null))
      {
        scala.Predef.require(this.internalPrototype.!=(null));
        this._elsep_=({
          <artifact> val qual$21: scala.reflect.core.Term = this.internalPrototype.elsep;
          <artifact> val x$107: scala.reflect.core.Term = this.internalPrototype.elsep;
          <artifact> val x$108: scala.reflect.core.Term.If = this;
          <artifact> val x$109: Map[scala.reflect.semantic.Host,scala.collection.immutable.Seq[Any]] = qual$21.internalCopy$default$3;
          <artifact> val x$110: reflect.core.Origin = qual$21.internalCopy$default$4;
          qual$21.internalCopy(x$107, x$108, x$109, x$110)
        })
      }
    else
      (): Unit);
    this._elsep
  };
  def hasElsep: Boolean = {
    (<empty>: Unit);
    this._hasElsep
  };
  def copy(cond: scala.reflect.core.Term = this.cond, thenp: scala.reflect.core.Term = this.thenp, elsep: scala.reflect.core.Term = this.elsep)(implicit origin: reflect.core.Origin): If.this.ThisType = Term.this.If.apply(cond, thenp, elsep)(scala.reflect.core.`package`.Origin.Transform.apply(this, this.origin));
  <synthetic> def copy$default$1: scala.reflect.core.Term = this.cond;
  <synthetic> def copy$default$2: scala.reflect.core.Term = this.thenp;
  <synthetic> def copy$default$3: scala.reflect.core.Term = this.elsep;
  override type ThisType = scala.reflect.core.Term.If;
  override def productPrefix: String = ("Term.If": String);
  override def productArity: Int = 3;
  override def productElement(n: Int): Any = n match {
    case 0 => this.cond
    case 1 => this.thenp
    case 2 => this.elsep
    case _ => throw new scala.`package`.IndexOutOfBoundsException(n.toString())
  };
  override def productIterator: Iterator[Any] = scala.runtime.ScalaRunTime.typedProductIterator[Nothing](this);
  override def canEqual(that: Any): Boolean = that.isInstanceOf[If.this.ThisType];
  override def equals(that: Any): Boolean = this.eq(that.asInstanceOf[AnyRef]);
  override def hashCode: Int = java.lang.System.identityHashCode(this)
};
@@<?> @@<?> object If extends scala.AnyRef {
  def <init>(): scala.reflect.core.Term.If.type = {
    If.super.<init>();
    ()
  };
  def apply(cond: scala.reflect.core.Term, thenp: scala.reflect.core.Term, elsep: scala.reflect.core.Term = null)(implicit origin: reflect.core.Origin): scala.reflect.core.Term.If = {
    def internal(cond: scala.reflect.core.Term, thenp: scala.reflect.core.Term, elsep: scala.reflect.core.Term, @org.scalareflect.ast.trivia @org.scalareflect.ast.auto hasElsep: Boolean): scala.reflect.core.Term.If = {
      <empty>;
      ({
        val result$macro$276: Boolean = cond.!=(null);
        if (result$macro$276)
          scala.Tuple2.apply[Boolean, scala.collection.immutable.Nil.type](true, immutable.this.Nil)
        else
          scala.Tuple2.apply[Boolean, List[String]](false, immutable.this.List.apply[String]("cond is equal to null"))
      } match {
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(true, _) => ()
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(false, (failures$macro$275 @ _)) => {
          org.scalareflect.invariants.InvariantFailedException.raise("cond.!=(null)", failures$macro$275, scala.Some.apply[scala.reflect.core.Term.If.type](If.this));
          ()
        }
      }: Unit);
      ({
        val result$macro$278: Boolean = thenp.!=(null);
        if (result$macro$278)
          scala.Tuple2.apply[Boolean, scala.collection.immutable.Nil.type](true, immutable.this.Nil)
        else
          scala.Tuple2.apply[Boolean, List[String]](false, immutable.this.List.apply[String]("thenp is equal to null"))
      } match {
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(true, _) => ()
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(false, (failures$macro$277 @ _)) => {
          org.scalareflect.invariants.InvariantFailedException.raise("thenp.!=(null)", failures$macro$277, scala.Some.apply[scala.reflect.core.Term.If.type](If.this));
          ()
        }
      }: Unit);
      ({
        val result$macro$280: Boolean = elsep.!=(null);
        if (result$macro$280)
          scala.Tuple2.apply[Boolean, scala.collection.immutable.Nil.type](true, immutable.this.Nil)
        else
          scala.Tuple2.apply[Boolean, List[String]](false, immutable.this.List.apply[String]("elsep is equal to null"))
      } match {
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(true, _) => ()
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(false, (failures$macro$279 @ _)) => {
          org.scalareflect.invariants.InvariantFailedException.raise("elsep.!=(null)", failures$macro$279, scala.Some.apply[scala.reflect.core.Term.If.type](If.this));
          ()
        }
      }: Unit);
      <empty>;
      <empty>;
      <empty>;
      <empty>;
      <empty>;
      val node: scala.reflect.core.Term.If = new Term.this.If(null, null, scala.collection.immutable.Map.apply[scala.reflect.semantic.Host, Nothing](), origin)((null: scala.reflect.core.Term), (null: scala.reflect.core.Term), (null: scala.reflect.core.Term), (hasElsep: Boolean));
      (node._cond_=(cond.internalCopy(cond, node, cond.internalCopy$default$3, cond.internalCopy$default$4)): Unit);
      (node._thenp_=(thenp.internalCopy(thenp, node, thenp.internalCopy$default$3, thenp.internalCopy$default$4)): Unit);
      (node._elsep_=(elsep.internalCopy(elsep, node, elsep.internalCopy$default$3, elsep.internalCopy$default$4)): Unit);
      (<empty>: Unit);
      node
    };
    internal(cond, thenp, if (elsep.!=(null))
      elsep
    else
      Lit.Unit.apply()(origin), elsep.!=(null))
  };
  <synthetic> def apply$default$3: scala.reflect.core.Term = null;
  def unapply(x: scala.reflect.core.Term.If): Option[(scala.reflect.core.Term, scala.reflect.core.Term, scala.reflect.core.Term)] = if (x.==(null))
    scala.None
  else
    scala.Some.apply[(scala.reflect.core.Term, scala.reflect.core.Term, scala.reflect.core.Term)](scala.Tuple3.apply[scala.reflect.core.Term, scala.reflect.core.Term, scala.reflect.core.Term](x.cond, x.thenp, x.elsep))
};
```